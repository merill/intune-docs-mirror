---
layout: Conceptual
title: Configure client status - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-status
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
description: Select client status settings in Configuration Manager.
ms.date: 2020-07-13T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 63ba3ba1-423a-f53a-bf2d-1ac0747c1b8e
document_version_independent_id: e9922919-2648-14d9-b36c-38f11d533f8a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/configure-client-status.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/configure-client-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/configure-client-status.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 7467763f-0d21-5254-e5c4-61553686daaf
---

# Configure client status - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you can monitor Configuration Manager clients and remediate problems, configure the site's client status settings. These settings specify the parameters that the site uses to mark clients as inactive. Also configure options to alert you if client activity falls below a specified threshold.

## Configure client status

1. In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Client Status** node. On the **Home** tab of the ribbon, in the **Client Status** group, select **Client Status Settings**.
2. Configure the following settings:

    Note

    If a client doesn't meet any of the settings, the site marks it as inactive.

    - **Client policy requests during the following days:** Specify the number of days since the client requested policy from the site. The default value is `7` days.

        Compare this value to the **Client policy polling interval** setting in the **Client Policy** group of client settings. Its default is 60 minutes. In other words, a client should poll the site for policy every hour. If it doesn't request policy after one week, the site marks it as inactive.
    - **Heartbeat discovery during the following days:** Specify the number of days since the client sent a heartbeat discovery record to the site. The default value is `7` days.

        Compare this value to the schedule for the [Heartbeat discovery method](../../servers/deploy/configure/about-discovery-methods). By default, the site runs heartbeat discovery once a week.
    - **Hardware inventory during the following days:** Specify the number of days since the client sent a hardware inventory record to the site. The default value is `7` days.

        Compare this value to the **Hardware inventory schedule** setting in the **Hardware Inventory** group of client settings. Its default is seven days.
    - **Software inventory during the following days:** Specify the number of days since the client sent a software inventory record to the site. The default value is `7` days.

        Compare this value to the **Schedule software inventory and file collection** setting in the **Software Inventory** group of client settings. Its default is seven days.
    - **Status messages during the following days:** Specify the number of days since the client sent any status messages to the site. The default value is `7` days. The client can send status messages for different kinds of activities, such as running a task sequence. The site deletes old status messages as part of the maintenance task, **Delete Aged Status Messages**.
3. Specify the following value to determine how long the site keeps client status history data:

    - **Retain client status history for the following number of days:** By default, the site keeps client status information for `31` days. This setting doesn't have any impact on client or site behavior. It's similar to a maintenance task for client status history.

## Configure the schedule

1. In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Client Status** node. On the **Home** tab of the ribbon, in the **Client Status** group, select **Schedule Client Status Update**.
2. Configure the interval at which you want client status to update.

    Note

    When you change the schedule for client status updates, it doesn't take effect until the next scheduled client status update on the previous schedule.

## Configure alerts

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Device Collections** node.
2. Select the collection for which you want to configure alerts. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.

    Note

    You can't configure alerts for user collections.
3. Switch to the **Alerts** tab, and select **Add**.

    Tip

    You can only view the **Alerts** tab if your security role has permissions for alerts.

    Choose the alerts that you want the site to generate for client status thresholds, and select **OK**.
4. In the **Conditions** list of the **Alerts** tab, select each client status alert, and then specify the following information:

    - **Alert Name**: Accept the default name or enter a new name for the alert.
    - **Alert Severity**: Choose the alert level that the Configuration Manager console displays.
    - **Raise alert**: Specify the threshold percentage for the alert.

## Automatic remediation exclusion

1. On the client computer where you want to disable automatic remediation, open the registry editor.

    Warning

    If you use the registry editor incorrectly, you can cause serious problems that could require you to reinstall Windows. Microsoft can't guarantee that you can solve problems that result from using the registry editor incorrectly. Use it at your own risk.
2. Navigate to the registry key **HKEY\_LOCAL\_MACHINE\Software\Microsoft\CCM\CcmEval**.
3. Change the value for the **NotifyOnly** entry:

    - `TRUE`: The client won't automatically remediate any problems that it finds. The site still notifies you in the **Monitoring** workspace about any problems with this client.
    - `FALSE`: This setting is the default. The client automatically remediates problems when it finds them, and the site notifies you in the **Monitoring** workspace.

When you install clients, you can exclude them from automatic remediation with the **NotifyOnly** installation property. For more information, see [About client installation properties](about-client-installation-properties).