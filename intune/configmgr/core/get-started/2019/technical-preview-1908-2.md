---
layout: Conceptual
title: Technical preview 1908.2 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1908-2
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1908.2.
ms.date: 2019-08-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 7b8c021b-b99f-210d-56ea-fa5cb5a6d99b
document_version_independent_id: 4e9d0f9f-bd9f-f87b-b080-764806ec2741
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1908-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1908-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1908-2.md
platformId: e1f41b58-ca5a-ff54-6d02-50f458f28a66
---

# Technical preview 1908.2 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1908.2. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Improvements to Console Connections

We've made the following improvements to **Console Connections**:

- The ability to message other administrators through Microsoft Teams.
- The **Last Console Heartbeat** column has replaced the **Last Connected Time**column.
    - An open console in the foreground sends a heartbeat every 10 minutes.

### Prerequisites

- The [Administration Service](../../plan-design/hierarchy/plan-for-the-sms-provider#administration-service) must be enabled for the **Last Console Heartbeat** to function.
- For messaging administrators, the account you want to message needs to have been discovered with [Microsoft Entra ID or AD User Discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

### Log files

For troubleshooting, refer to the **SmsAdminUI.log**.

### Known issues

The error message notifying you that Microsoft Teams isn't installed won't be displayed if the following Registry key doesn't exist:

Computer\HKEY\_CURRENT\_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

To work around the issue, manually create the Registry key.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Go to **Administration** &gt; **Security** &gt; **Console Connections**.
2. Notice the column **Last Console Heartbeat** has replaced the **Last Connected Time** column.
3. Right-click on a user's console connection and select **Message Administrator**.
    - If the User Principal Name isn't found for the selected administrator, **Message Administrator** is grayed out.
    - An error message, including a download link, appears if Microsoft Teams isn't installed on the device from which you run the console.
    - If Microsoft Teams is installed on the device from which you run the console, it will open a chat with the user.

![Message administrators with Microsoft Teams screenshot](media/4923997-message-administrator.png)

## Improvements to multicast-enabled distribution points

You can now enable multicast on a distribution point without installing Windows Deployment Services (WDS). Because WDS isn't required, the multicast-enabled distribution point can be a client or server OS, including Windows Server Core. It can also receive multicast content in the full OS, it's not limited to only Windows PE.

### Prerequisites

The distribution point and Configuration Manager client use the following network ports:

- TCP 27500-27755
- UDP 27500-27755
- UDP 64001-64256

Make sure your network infrastructure allows the use of these ports.

Note

You don't have to enable the PXE responder. In this release, when you enable multicast, it always uses this new multicast server.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Enable multicast on the distribution point

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Distribution Points** node. Select the target distribution point, and select **Properties** in the ribbon.
2. Switch to the **Multicast** tab, and select the option to **Enable multicast to simultaneously send data to multiple clients**.
3. Select **OK** to save the settings.

For more information about the additional multicast settings, see [Install and configure distribution points](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-multicast).

#### Enable packages to use multicast

The following content types support multicast:

- Packages
- Driver packages
- OS images
- OS upgrade packages

Enable any package that you want to distribute via multicast:

1. Open the **Properties** of the target package and switch to the **Distribution Settings** tab.
2. In the OS deployment settings section, enable the option to **Allow this package to be transferred via multicast**.

Distribute these multicast-enabled packages to a multicast-enabled distribution point.

#### Deploy a task sequence

Configure a task sequence deployment that references these multicast-enabled packages. On the **Distribution Points** tab of the deployment properties, select the deployment option to **Download content locally when needed by the running task sequence**.

For more information, see [Deploy a task sequence](../../../osd/deploy-use/deploy-a-task-sequence).

#### Monitor the multicast deployment

On the distribution point, there's a new log file, **McsServer.log**. This file includes details of multicast download sessions.

On the client, review the **smsts.log** file for entries from the **McsClient** component.

### Known issues

After you configure multicast on a distribution point, confirm the following settings in the registry key `HKLM\Software\Microsoft\SMS\DP`:

- The value `IsMulticast` should be `1`.
- The permissions on the `SccmMcs` key should have the **Local Service** account with **Full Control**.

This multicast provider doesn't support IPv6. Disable the IPv6 protocol on any multicast-enabled distribution point.

## Optimizations to the CMPivot engine

We've added some significant optimizations to the CMPivot engine that allows us to push more of the processing to the ConfigMgr client. The optimizations drastically reduce the network and server CPU load needed to run CMPivot queries. With these optimizations, we can now sift through gigabytes of client data in real time.

### Examples

You can search all event logs on all clients in your enterprise for authentication failures with the following query:

```Kusto
EventLog('Security')
| where  EventID == 4673
| summarize count() by Device
| order by count_ desc
```

Search for a file by hash:

```Kusto
Device
| join kind=leftouter ( File('%windir%\\system32\\*.exe')
| where Hash == 'A92056D772260B39A876D01552496B2F8B4610A0B1E084952FE1176784E2CE77')
| project Device, MalwareFound = iif( isnull(FileName), 'No', 'Yes')
```

## Set keyboard layout during OS deployment

Based on your feedback, you can now set the default keyboard layout during an OS deployment task sequence. The **Apply Windows Settings** task sequence step includes the setting to **Set default keyboard layout in Windows**.