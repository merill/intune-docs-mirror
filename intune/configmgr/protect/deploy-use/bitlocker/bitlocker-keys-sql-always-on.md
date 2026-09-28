---
layout: Conceptual
title: Using SQL Always On when BitLocker recovery data is encrypted in the database - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/bitlocker-keys-sql-always-on
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Describes how to use SQL Always On when BitLocker recovery data is encrypted in the database
ms.date: 2025-06-12T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 387f6289-7af0-b2c1-ed12-9c660b477c00
document_version_independent_id: 387f6289-7af0-b2c1-ed12-9c660b477c00
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/bitlocker-keys-sql-always-on.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/bitlocker-keys-sql-always-on
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/bitlocker-keys-sql-always-on.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 0317d312-3b6b-f71b-b54b-cca2e732e009
---

# Using SQL Always On when BitLocker recovery data is encrypted in the database - Configuration Manager | Microsoft Learn

For SQL Always On, additional steps are required when the BitLocker information is encrypted using the instructions at [Encrypt recovery data in the database](encrypt-recovery-data). The additional steps ensure that all Always On nodes can automatically open the Database Master Key (DMK) when a failover event occurs. Following steps allows seamless retrieval of BitLocker keys without manual intervention.

## Overview of SQL Always On when BitLocker recovery data is encrypted in the database

SQL Server encrypts data using a hierarchical infrastructure and is described in depth at [Encryption Hierarchy](/en-us/sql/relational-databases/security/encryption/encryption-hierarchy).

- **Site Master Key (SMK)** - This key is a *per instance* key that is unique to each SQL Server Always On node and isn't replicated. It's used to encrypt the database master key.
- **Database Master Key (DMK)** - This key is stored in the database and is replicated. It's used to encrypt the BitLockerManagement\_CERT.
- **BitLockerManagement\_CERT** - This certificate is stored in the database and is replicated. It's used to encrypt some BitLocker-related data like recovery keys.

The SMK encrypts the DMK password. SMKs are node-specific. When a failover event occurs, the new primary node can't decrypt the DMK password since it was encrypted with a different SMK. Setting the DMK password on each node allows the node to decrypt the password on failover.

Note

The BitLockerManagement\_CERT performs the encryption of the columns. If this certificate is lost or deleted, or the DMK that encrypted it's lost or deleted, BitLocker keys have to be escrowed and re-encrypted again.

## If the Database Master Key (DMK) password is known

Execute the following command on each node in the Availability Group that hosts the Configuration Manager database:

Important

In the following command:

- Replace `password` everywhere with a strong password of your choosing. Make sure to securely store the password for future reference.
- Replace `CM_XXX` with the name of the Configuration Manager (CM) database.

```sql
EXEC sp_control_dbmasterkey_password
    @db_name = N'CM_XXX',
    @password = N'password',
    @action = N'add';
```

This command registers the DMK password with the local Service Master Key (SMK) allowing SQL Server to automatically open the DMK when a failover event occurs. This process ensures the DMK can be decrypted automatically on that node after a failover or a restart.

To verify that all nodes can automatically open the Database Master Key (DMK) and decrypt the data, see the section Verify all nodes can automatically open the Database Master Key (DMK) and decrypt the data in this article.

## If the existing Database Master Key (DMK) password is unknown

If the existing DMK password is unknown, the existing DMK must be dropped and a new one created with a known password. These steps document how to perform this procedure.

### Find a valid DMK

If it's unknown which node has a valid DMK, follow these steps to determine where the existing DMK is open:

Important

In the following queries and commands:

- Replace `password` everywhere with a strong password of your choosing. Make sure to securely store the password in a known location for future reference.
- Replace `CM_XXX` with the name of the Configuration Manager (CM) database.

1. Run the following query on the primary node:

    ```sql
    SELECT TOP 5 RecoveryAndHardwareCore.DecryptString(RecoveryKey, DEFAULT)
    FROM RecoveryAndHardwareCore_Keys
    ORDER BY LastUpdateTime DESC
    ```
2. In the resultant query:

    - If the DMK is open, the query returns plaintext values for any rows that have a valid key in them. This node is the node to start on and the next step can be skipped.
    - If the DMK isn't open, the query returns NULL values for all rows. The current node isn't the node where the DMK is open. Follow the next step to find the node where the DMK is open.
3. If the query returns all NULL values, then failover to each secondary node and repeat the previous steps until the node that can successfully decrypt **RecoveryAndHardwareCore\_Keys** is found. This node is the node to start on.

### Create a new Database Master Key (DMK)

Once the proper node with the open DMK is identified, follow these steps:

1. On the node that was identified in the previous steps, run the following query to export the BitLockerManagement\_CERT certificate with its private key. Make sure to use a strong password:

    ```sql
    BACKUP CERTIFICATE BitLockerManagement_CERT
    TO FILE = 'C:\Windows\Temp\BitLockerManagement_CERT'
    WITH PRIVATE KEY
    (
        FILE = 'C:\Windows\Temp\BitLockerManagement_CERT_KEY',
        ENCRYPTION BY PASSWORD = 'password'
    );
    ```
2. Back up the existing Database Master Key (DMK) by running the following query to export the existing DMK:

    ```sql
    BACKUP MASTER KEY
    TO FILE = 'C:\Windows\Temp\DMK'
    ENCRYPTION BY PASSWORD = 'password';
    ```

    Note

    This step is optional but recommended. Make sure to keep the backup in a secure known location.
3. Run the following query to drop the existing certificate and DMK:

    ```sql
    DROP CERTIFICATE BitLockerManagement_CERT;
    DROP MASTER KEY;
    ```

    This step removes the old keys.
4. Run the following query to create a new DMK. Make sure to use a strong password:

    ```sql
    CREATE MASTER KEY
    ENCRYPTION BY PASSWORD = 'password';
    ```
5. Run the following query to register the new DMK password with the local SMK:

    ```sql
    EXEC sp_control_dbmasterkey_password
        @db_name = N'CM_XXX',
        @password = N'password',
        @action = N'add';
    ```
6. Run the following query to import the previously exported BitLockerManagement\_CERT certificate:

    ```sql
    CREATE CERTIFICATE BitLockerManagement_CERT AUTHORIZATION RecoveryAndHardwareCore
    FROM FILE = 'C:\Windows\Temp\BitLockerManagement_CERT'
    WITH PRIVATE KEY
    (
        FILE = 'C:\Windows\Temp\BitLockerManagement_CERT_KEY',
        DECRYPTION BY PASSWORD = 'password'
    );
    ```
7. Run the following query to grant required control permissions on the certificate:

    ```sql
    GRANT CONTROL ON CERTIFICATE::BitLockerManagement_CERT TO RecoveryAndHardwareRead;
    GRANT CONTROL ON CERTIFICATE::BitLockerManagement_CERT TO RecoveryAndHardwareWrite;
    ```
8. Fail over to the next node.
9. Run the following query to register the DMK password with the local SMK. Execute once per replica:

    ```sql
    EXEC sp_control_dbmasterkey_password
        @db_name = N'CM_XXX',
        @password = N'password',
        @action = N'add';
    ```
10. Perform the previous two steps on any remaining nodes.
11. Fail over to the original node.
12. To verify that all nodes can automatically open the Database Master Key (DMK) and decrypt the data, see the next section Verify all nodes can automatically open the Database Master Key (DMK) and decrypt the data in this article.

## Verify all nodes can automatically open the Database Master Key (DMK) and decrypt the data

To verify that all nodes can automatically open the Database Master Key (DMK) and decrypt the data:

1. Fail over to a node.
2. Run the following query:

    ```sql
    SELECT TOP 5 RecoveryAndHardwareCore.DecryptString(RecoveryKey, DEFAULT)
    FROM RecoveryAndHardwareCore_Keys
    ORDER BY LastUpdateTime DESC
    ```
3. If the query returns plaintext values for any rows that have a valid key in them, then the node can automatically open the Database Master Key (DMK) and can decrypt the data.
4. Repeat the previous three steps for each additional node.

Tip

For improved security, store the strong DMK password securely. For example, in Azure Key Vault or another secure secret store. Additionally, avoid hardcoding the DMK password in plain text in scripts or configuration files.