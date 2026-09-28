---
layout: Conceptual
title: Monitor Endpoint Protection status - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/monitor-endpoint-protection
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
description: Learn how monitor Endpoint Protection in your Configuration Manager hierarchy.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 197fd3ea-92eb-9e9a-0803-345728622dd5
document_version_independent_id: e19c917e-55d0-4049-ae4c-a9ab46490d6d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/monitor-endpoint-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/monitor-endpoint-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/monitor-endpoint-protection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 1dc51bcd-99c4-070c-19f8-a22513e2b634
---

# Monitor Endpoint Protection status - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can monitor Endpoint Protection in your Microsoft Configuration Manager hierarchy by using the **Endpoint Protection Status** node under **Security** in the **Monitoring** workspace, the **Endpoint Protection** node in the **Assets and Compliance** workspace, and by using reports.

## How to Monitor Endpoint Protection by Using the Endpoint Protection Status Node

1. In the Configuration Manager console, click **Monitoring**.
2. In the **Monitoring** workspace, expand **Security** and then click **Endpoint Protection Status**.
3. In the **Collection** list, select the collection for which you want to view status information.

    Important

    Collections are available for selection in the following cases:

    - When you select **View this collection in the Endpoint Protection dashboard** on the **Alerts** tab of the *&lt;collection name&gt;***Properties**dialog box.
        - When you deploy an Endpoint Protection antimalware policy to the collection.
        - When you enable and deploy Endpoint Protection client settings to the collection.
4. Review the information that is displayed in the **Security State** and **Operational State** sections. You can click any status link to create a temporary collection in the **Devices** node in the **Assets and Compliance** workspace. The temporary collection contains the computers with the selected status.

    Important

    Information that is displayed in the **Endpoint Protection Status** node is based on the last data that was summarized from the Configuration Manager database and might not be current. If you want to retrieve the latest data, on the **Home** tab, click **Run Summarization**, or click **Schedule Summarization** to adjust the summarization interval.

## How to Monitor Endpoint Protection in the Assets and Compliance Workspace

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, perform one of the following actions:

    - Click **Devices**. In the **Devices** list, select a computer, and then click the **Malware Detail** tab.
    - Click **Device Collections**. In the **Device Collections** list, select the collection that contains the computer you want to monitor and then, on the **Home** tab, in the **Collection** group, click **Show Members**.
3. In the *&lt;collection name&gt;* list, select a computer, and then click the **Malware Detail** tab.

## How to Monitor Endpoint Protection by Using Reports

Use the following reports to help you view information about Endpoint Protection in your hierarchy. You can also use these reports to help troubleshoot any Endpoint Protection problems. For more information about how to configure reporting in Configuration Manager, see [Introduction to reporting](../../core/servers/manage/introduction-to-reporting) and [Log files](../../core/plan-design/hierarchy/log-files). The Endpoint Protection reports are in the Endpoint Protection folder.

| Report name | Description |
| --- | --- |
| **Antimalware Activity Report** | Displays an overview of antimalware activity for a specified collection. |
| **Infected Computers** | Displays a list of computers on which a specified threat is detected. |
| **Top Users By Threats** | Displays a list of users with the most number of detected threats. |
| **User Threat List** | Displays a list of threats that were found for a specified user account. |

## Malware Alert Levels

Use the following table to identify the different Endpoint Protection alert levels that might be displayed in reports, or in the Configuration Manager console.

| Alert level | Description |
| --- | --- |
| **Failed** | Endpoint Protection failed to remediate the malware. Check your logs for details of the error.**Note:** For a list of Configuration Manager and Endpoint Protection log files, see the "Endpoint Protection" section in the [Log files](../../core/plan-design/hierarchy/log-files) topic. |
| **Removed** | Endpoint Protection successfully removed the malware. |
| **Quarantined** | Endpoint Protection moved the malware to a secure location and prevented it from running until you remove it or allow it to run. |
| **Cleaned** | The malware was cleaned from the infected file. |
| **Allowed** | An administrative user selected to allow the software that contains the malware to run. |
| **No Action** | Endpoint Protection took no action on the malware. This might occur if the computer is restarted after malware is detected and the malware is no longer detected; for instance, if a mapped network drive on which malware is detected is not reconnected when the computer restarts. |
| **Blocked** | Endpoint Protection blocked the malware from running. This might occur if a process on the computer is found to contain malware. |