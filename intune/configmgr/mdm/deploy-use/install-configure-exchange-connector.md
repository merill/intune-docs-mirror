---
layout: Conceptual
title: Install the Exchange connector - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/install-configure-exchange-connector
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
description: Install and configure the Exchange connector for Configuration Manager to manage mobile devices via ActiveSync.
ms.date: 2019-12-31T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 823121f8-69af-29c0-e734-a32880be9084
document_version_independent_id: 3a25bec4-bf65-9eac-8e21-e2990613cf31
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/install-configure-exchange-connector.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/install-configure-exchange-connector
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/install-configure-exchange-connector.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 5fc6d5e9-3e4f-0fb4-263d-857a24535b92
---

# Install the Exchange connector - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use this procedure to install and configure an Exchange Server connector to manage mobile devices. Configuration Manager supports only one connector in an Exchange organization.

Before you install the Exchange Server connector for Configuration Manager, make sure you have the required permissions and versions. For more information, see [Device management with Exchange and Configuration Manager](manage-mobile-devices-with-exchange-activesync#prerequisites).

## Exchange connection account

Decide which account will connect to the Exchange Client Access server to manage the mobile devices. The account can be the computer account of the site server or a Windows user account.

Then, configure this account in an Exchange role group to run the following Exchange Server cmdlets:

- **Clear-ActiveSyncDevice**
- **Get-ActiveSyncDevice**
- **Get-ActiveSyncDeviceAccessRule**
- **Get-ActiveSyncDeviceStatistics**
- **Get-ActiveSyncMailboxPolicy**
- **Get-ActiveSyncOrganizationSettings**
- **Get-ExchangeServer**
- **Get-Mailbox**
- **Get-Recipient**
- **Set-ADServerSettings**
- **Set-ActiveSyncDeviceAccessRule**
- **Set-ActiveSyncMailboxPolicy**
- **Set-CASMailbox**
- **New-ActiveSyncDeviceAccessRule**
- **New-ActiveSyncMailboxPolicy**
- **Remove-ActiveSyncDevice**
- **Get-CasMailbox**
- **Get-User**
- **Set-ActiveSyncOrganizationSettings**

The following Exchange Server management roles include these cmdlets:

- Recipient Management
- View-Only Organization Management
- Server Management

For more information, see [Understanding management role groups](/en-us/exchange/understanding-management-role-groups-exchange-2013-help) in the Exchange Server 2013 documentation.

Tip

If you try to install or use the Exchange Server connector without the required cmdlets, you'll see the following error in the EasDisc.log file on the site server computer: `Invoking cmdlet <cmdlet> failed`.

## Install the connector

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and then select **Exchange Server Connectors**.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Add Exchange Server**.
3. On the **General** page of the Add Exchange Server wizard, select one of the Exchange Server environments:

    - **On-premises Exchange Server**: Specify a single server or a Client Access Server array for each Active Directory site.

        If the server or the array is offline, Configuration Manager tries to discover a Client Access Server to use. If that fails, Configuration Manager falls back to using a mailbox server to make a connection to a Client Access Server. When it retries the connection, it logs the following warnings in the EasDisc.log file on the site server computer: `Failed to open runspace for site <site_name>`.
    - **Hosted Exchange Server**: Specify the server address of your Exchange Online environment.

    Then select the primary site to run the Exchange Server connector.
4. On the **Account** page, specify the account to connect to the Exchange Server. For more information, see Exchange connection account.
5. On the **Discovery** page, configure the synchronization schedule and rules for finding devices.
6. On the **Settings** page, configure the mobile device settings in the following groups:

    - **General**
    - **Password**
    - **Email Management**
    - **Security**
    - **Application**

    For more information, see [Exchange connector settings](manage-mobile-devices-with-exchange-activesync#policies).

    If you also enroll mobile devices by using Configuration Manager [on-premises MDM](../understand/manage-mobile-devices-with-on-premises-infrastructure), enable the option to **Allow external mobile device management**. This setting allows these mobile devices to continue receiving email from Exchange after Configuration Manager enrolls them.
7. Complete the wizard.

## Verify and monitor

Verify the installation of the Exchange Server connector with status messages and log files:

- Confirm that Site Component Manager successfully installed the Exchange Server connector. Look for message status ID **1015** from the **SMS\_EXCHANGE\_CONNECTOR** component.

    The installation can fail if the specified Client Access Server is offline. If Configuration Manager can't successfully install the connector, Configuration Manager retries the installation every 60 minutes. It continues to retry until the installation succeeds or you remove the Exchange Server connector.
- On the site server computer, review **SiteComp.log** for the following entry: `Component SMS_EXCHANGE_CONNECTOR flagged for installation`. It then logs the successful installation with the following text: `STATMSG: ID=1015`.

After you complete the installation, monitor the mobile devices that are found and managed by the connector. View the collections of mobile devices, and use the reports for mobile devices.

Note

Configuration Manager generates names for the mobile devices that it finds. It uses the format *user name*\_*device type*. For example, **jdoe\_WindowsPhone**. If a user has more than one mobile device that has the same device type, Configuration Manager displays the same name for these mobile devices in the console and in reports.