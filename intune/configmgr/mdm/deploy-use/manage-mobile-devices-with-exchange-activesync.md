---
layout: Conceptual
title: Device management with Exchange - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync
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
description: Manage mobile devices with the Exchange Server connector in Configuration Manager.
ms.date: 2019-12-31T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c5ba2435-7ec6-45c4-e87b-02009e663c45
document_version_independent_id: cd18ab8c-4ce1-3828-2f5c-d96da705ad85
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 491bbc23-f815-0f99-c3f3-6a7c1798d83a
---

# Device management with Exchange - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If you have mobile devices that you connect to Exchange Server via the ActiveSync protocol, you can use the Exchange Server connector in Configuration Manager to manage these devices. The connector works with both on-premises Exchange Server or Exchange Online. Use the Configuration Manager console to configure Exchange mobile device management features. For example, remote device wipe and settings control for multiple Exchange servers.

![Logical diagram of Exchange Server connector with Configuration Manager](media/configmgr-with-exchange.png)

When you manage mobile devices with this connector, it doesn't install the Configuration Manager client or enroll the devices via MDM. The management functions of Exchange Server are limited in comparison to these other options. For example, you can't install software or use configuration items to configure these devices. For more information, see [Choose a device management solution for Configuration Manager](../../core/plan-design/choose-a-device-management-solution).

## Policies

When you use the connector, Configuration Manager configures settings on the mobile devices. The devices don't use the default Exchange ActiveSync mailbox policies. Define the settings that you want to use in the following groups:

- **General**
- **Password**
- **Email Management**
- **Security**
- **Application**

For example, in the **Password** group, you can configure the following settings:

- Whether mobile devices require a password
- The minimum password length
- Password complexity
- Whether password recovery is allowed

When you configure at least one setting in the group, Configuration Manager manages all settings in the group for mobile devices. If you don't configure any setting in a group, Exchange continues to manage those settings for the mobile devices. Any Exchange ActiveSync mailbox policies that you configure on the Exchange Server and assign to users are still applied.

## Access rules and remote actions

You can also configure the Exchange Server connector to manage the Exchange access rules. These access rules include allow, block, or quarantine mobile devices. You can remotely wipe mobile devices by using the Configuration Manager console.

Tip

When a mobile device is transferred to another user, before the new owner configures their Exchange account on the device, delete the mobile device from the Configuration Manager console.

## Prerequisites

Important

Before you install this connector, confirm that Configuration Manager supports your version of Exchange. For more information, see [Supported configurations - Exchange Server connector](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ExSrvConOS).

### Permissions to configure the connector

You need the following security permissions to configure the Exchange Server connector in Configuration Manager:

- To add, modify, and delete the Exchange Server connector: **Modify** permission for the **Site** object.
- To configure the mobile device settings: **ModifyConnectorPolicy** permission for the **Site** object.

For example, the **Full Administrator** built-in role includes these required permissions.

### Permissions to manage mobile devices

You need the following security permissions to manage mobile devices:

- To wipe a mobile device: **Delete resource** for the **Collection** object.
- To cancel a wipe command: **Modify resource** for the **Collection** object.
- To allow and block mobile devices: **Modify resource** for the **Collection** object.

For example, the **Operations Administrator** built-in role includes these required permissions.

For more information, see [Configure role-based administration](../../core/servers/deploy/configure/configure-role-based-administration).