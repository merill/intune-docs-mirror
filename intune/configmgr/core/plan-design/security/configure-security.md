---
layout: Conceptual
title: Configure security - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/configure-security
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
description: How to configure security-related options for Configuration Manager.
ms.date: 2021-12-21T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 1dc1b7c8-1005-c581-b9d5-dd3769fb3ca5
document_version_independent_id: 85c42241-97da-f8d4-39f5-48f60f2a47dd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/configure-security.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/configure-security
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/configure-security.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: a7c361fc-d04d-c771-10c4-aef92bd1f337
---

# Configure security - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information in this article to help you set up security-related options for Configuration Manager. Before you start, make sure you have a [Plan for security](plan-for-security).

Important

Starting in Configuration Manager version 2103, sites that allow HTTP client communication are deprecated. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http).

## Client PKI certificates

If you want to use public key infrastructure (PKI) certificates for client connections to site systems that use Internet Information Services (IIS), use the following procedure to configure settings for these certificates.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node. Select the primary site to configure.
2. In the ribbon, choose **Properties**. Then switch to the **Communication Security** tab.
3. Select the settings for site systems that use IIS.

    - **HTTPS only**: Clients that are assigned to the site always use a client PKI certificate when they connect to site systems that use IIS. For example, a management point and distribution point.
    - **HTTPS or HTTP**: You don't require clients to use PKI certificates.
    - **Use Configuration Manager-generated certificates for HTTP site systems**: For more information on this setting, see [Enhanced HTTP](../hierarchy/enhanced-http).
4. Select the settings for client computers.

    - **Use client PKI certificate (client authentication capability) when available**: If you chose the **HTTPS or HTTP** site server setting, choose this option to use a client PKI certificate for HTTP connections. The client uses this certificate instead of a self-signed certificate to authenticate itself to site systems. If you chose **HTTPS only**, this option is automatically chosen.

        When more than one valid PKI client certificate is available on a client, select **Modify** to configure the client certificate selection methods. For more information about the client certificate selection method, see [Planning for PKI client certificate selection](plan-for-certificates#pki-client-certificate-selection).
    - **Clients check the certificate revocation list (CRL) for site systems**: Enable this setting for clients to check your organization's CRL for revoked certificates. For more information about CRL checking for clients, see [Planning for PKI certificate revocation](plan-for-certificates#pki-certificate-revocation).
5. To import, view, and delete the certificates for trusted root certification authorities, select **Set**. For more information, see [Planning for the PKI trusted root certificates and the certificate issuers List](plan-for-certificates#pki-trusted-root-certificates).

Repeat this procedure for all primary sites in the hierarchy.

## Manage the trusted root key

Use these procedures to pre-provision and verify the trusted root key for a Configuration Manager client.

Note

If clients can get the trusted root key from Active Directory Domain Services or client push, you don't have to pre-provision it.

When clients use HTTPS communication to management points, you don't have to pre-provision the trusted root key. They establish trust by the PKI certificates.

For more information on the trusted root key, see [Plan for security](plan-for-security#the-trusted-root-key).

### Pre-provision a client with the trusted root key by using a file

1. On the site server, browse to the Configuration Manager installation directory. In the `\bin\<platform>` subfolder, open the following file in a text editor: `mobileclient.tcf`
2. Locate the entry, `SMSPublicRootKey`. Copy the value from that line, and close the file without saving any changes.
3. Create a new text file, and paste the key value that you copied from the mobileclient.tcf file.
4. Save the file in a location where all computers can access it, but where the file is safe from tampering.
5. Install the client by using any installation method that accepts client.msi properties. Specify the following property: `SMSROOTKEYPATH=<full path and file name>`

    Important

    When you specify the trusted root key during client installation, also specify the site code. Use the following client.msi property: `SMSSITECODE=<site code>`

### Pre-provision a client with the trusted root key without using a file

1. On the site server, browse to the Configuration Manager installation directory. In the `\bin\<platform>` subfolder, open the following file in a text editor: `mobileclient.tcf`
2. Locate the entry, `SMSPublicRootKey`. Copy the value from that line, and close the file without saving any changes.
3. Install the client by using any installation method that accepts client.msi properties. Specify the following client.msi property: `SMSPublicRootKey=<key>` where `<key>` is the string that you copied from mobileclient.tcf.

    Important

    When you specify the trusted root key during client installation, also specify the site code. Use the following client.msi property: `SMSSITECODE=<site code>`

### Verify the trusted root key on a client

1. Open a Windows PowerShell console as an administrator.
2. Run the following command:

    ```PowerShell
    (Get-WmiObject -Namespace root\ccm\locationservices -Class TrustedRootKey).TrustedRootKey
    ```

The returned string is the trusted root key. Verify that it matches the **SMSPublicRootKey** value in the mobileclient.tcf file on the site server.

### Remove or replace the trusted root key

Remove the trusted root key from a client by using the client.msi property, `RESETKEYINFORMATION = TRUE`.

To replace the trusted root key, reinstall the client together with the new trusted root key. For example, use client push, or specify the client.msi property **SMSPublicRootKey**.

For more information on these installation properties, see [About client installation parameters and properties](../../clients/deploy/about-client-installation-properties).

## Signing and encryption

Configure the most secure signing and encryption settings for site systems that all clients in the site can support. These settings are especially important when you let clients communicate with site systems by using self-signed certificates over HTTP.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node. Select the primary site to configure.
2. In the ribbon, select **Properties**, and then switch to the **Signing and Encryption** tab.

    This tab is available on a primary site only. If you don't see the **Signing and Encryption** tab, make sure that you're not connected to a central administration site or a secondary site.
3. Configure the signing and encryption options for clients to communicate with the site.

    - **Require signing**: Clients sign data before sending to the management point.
    - **Require SHA-256**: Clients use the SHA-256 algorithm when signing data.

        Warning

        Don't **Require SHA-256** without first confirming that all clients support this hash algorithm. These clients include ones that might be assigned to the site in the future.

        If you choose this option, and clients with self-signed certificates can't support SHA-256, Configuration Manager rejects them. The SMS\_MP\_CONTROL\_MANAGER component logs the message ID 5443.
    - **Use encryption**: Clients encrypt client inventory data and status messages before sending to the management point.

Repeat this procedure for all primary sites in the hierarchy.

## Role-based administration

Role-based administration combines security roles, security scopes, and assigned collections to define the administrative scope for each administrative user. A scope includes the objects that a user can view in the console, and the tasks related to those objects that they have permission to do. Role-based administration configurations are applied at each site in a hierarchy.

For more information, see [Configure role-based administration](../../servers/deploy/configure/configure-role-based-administration). This article details the following actions:

- Create custom security roles
- Configure security roles
- Configure security scopes for an object
- Configure collections to manage security
- Create a new administrative user
- Modify the administrative scope of an administrative user

Important

Your own administrative scope defines the objects and settings that you can assign when you configure role-based administration for another administrative user. For information about planning for role-based administration, see [Fundamentals of role-based administration](../../understand/fundamentals-of-role-based-administration).

## Manage accounts

Configuration Manager supports Windows accounts for many different tasks and uses. To view accounts that are configured for different tasks, and to manage the password that Configuration Manager uses for each account, use the following procedure:

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Security**, and then choose the **Accounts** node.
2. To change the password for an account, select the account in the list. Then choose **Properties** in the ribbon.
3. Choose **Set** to open the **Windows User Account** dialog box. Specify the new password for Configuration Manager to use for this account.

    Note

    The password that you specify must match this account's password in Active Directory.

For more information, see [Accounts used in Configuration Manager](../hierarchy/accounts).

## Microsoft Entra ID

Integrate Configuration Manager with Microsoft Entra ID to simplify and cloud-enable your environment. Enable the site and clients to authenticate by using Microsoft Entra ID.

For more information, see the **Cloud Management** service in [Configure Azure services](../../servers/deploy/configure/azure-services-wizard).

## SMS Provider authentication

You can specify the minimum authentication level for administrators to access Configuration Manager sites. This feature enforces administrators to sign in to Windows with the required level before they can access Configuration Manager. For more information, see [Plan for SMS Provider authentication](plan-for-security#sms-provider-authentication).

Important

This configuration is a hierarchy-wide setting. Before you change this setting, make sure that all Configuration Manager administrators can sign in to Windows with the required authentication level.

To configure this setting, use the following steps:

1. First sign in to Windows with the intended authentication level.
2. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
3. Select **Hierarchy Settings** in the ribbon.
4. Switch to the **Authentication** tab. Select the desired [authentication level](plan-for-security#sms-provider-authentication), and then select **OK**.

    - Only when necessary, select **Add** to exclude specific users or groups. For more information, see Exclusions.

### Exclusions

From the **Authentication** tab of Hierarchy Settings, you can also exclude certain users or groups. Use this option sparingly. For example, when specific users require access to the Configuration Manager console, but can't authenticate to Windows at the required level. It may also be necessary for automation or services that run under the context of a system account.