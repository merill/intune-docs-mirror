---
layout: Conceptual
title: Configure Endpoint Protection alerts - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-configure-alerts
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
description: Learn how to configure Endpoint Protection alerts in Configuration Manager.
ms.date: 2017-03-23T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: edea2675-78a7-ee43-b270-7ad488d04948
document_version_independent_id: 545d518c-9ff9-63b6-a1b6-6445fe93699f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-configure-alerts.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-configure-alerts
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-configure-alerts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 4a9738fd-e60d-6261-4e49-7e9742cf037a
---

# Configure Endpoint Protection alerts - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can configure Endpoint Protection alerts in Microsoft Configuration Manager to notify administrative users when specific events, such as a malware infection, occur in your hierarchy. Notifications display in the Endpoint Protection dashboard in the Configuration Manager console in the **Alerts** node of the **Monitoring** workspace, or can be emailed to specified users.

Use the following steps and the supplemental procedures in this topic to configure alerts for Endpoint Protection in Configuration Manager.

Important

You must have the **Enforce Security** permission for collections to configure Endpoint Protection alerts.

## Steps to Configure Alerts for Endpoint Protection in Configuration Manager

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, click **Device Collections**.
3. In the **Device Collections** list, select the collection for which you want to configure alerts, and then on the **Home** tab, in the **Properties** group, click **Properties**.

    Note

    You cannot configure alerts for user collections.
4. On the **Alerts** tab of the *&lt;Collection Name&gt;***Properties** dialog box, select **View this collection in the Endpoint Protection dashboard** if you want to view details about antimalware operations for this collection in the **Monitoring** workspace of the Configuration Manager console.

    Note

    This option is unavailable for the **All Systems** collection.
5. On the **Alerts** tab of the *&lt;Collection Name&gt;***Properties** dialog box, click **Add**.
6. In the **Add New Collection Alerts** dialog box, in the **Generate an alert when these conditions apply** section, select the alerts that you want Configuration Manager to generate when the specified Endpoint Protection events occur, and then click **OK**.
7. In the **Conditions** list of the **Alerts** tab, select each Endpoint Protection alert, and then specify the following information:

    - **Alert Name** - Accept the default name or enter a new name for the alert.
    - **Alert Severity** - In the list, select the alert level to display in the Configuration Manager console.
8. Depending on the alert that you select, specify the following additional information:

    - **Malware detection** - This alert is generated if malware is detected on any computer in the collection that you monitor. The **Malware detection threshold** specifies the malware detection levels at which this alert is generated:

        - **High - All detections** - The alert is generated when there are one or more computers in the specified collection on which any malware is detected, regardless of what action the Endpoint Protection client takes.
        - **Medium - Detected, pending action** - The alert is generated when there is one or more computers in the specified collection on which malware is detected, and you must manually remove the malware.
        - **Low - Detected, still active** - The alert is generated when there are one or more computers in the specified collection on which malware is detected and is still active.
    - **Malware outbreak** - This alert is generated if specified malware is detected on a specified percentage of computers in the collection that you monitor.

        - **Percentage of computers with malware detected** - The alert is generated when the percentage of computers with malware that is detected in the collection exceeds the percentage that you specify. Specify a percentage from **1** through **99**.

            Note

            The percentage value is based on the number of computers in the collection, but excludes computers that do not have a Configuration Manager client installed. It includes computers that do not yet have the Endpoint Protection client installed.
    - **Repeated malware detection** - This alert is generated if specific malware is detected more than a specified number of times over a specified number of hours on the computers in the collection that you monitor. Specify the following information to configure this alert:

        - **Number of times malware has been detected:** - The alert is generated when the same malware is detected on computers in the collection more than the specified number of times. Specify a number from **2** through **32**.
        - **Interval for detection (hours):** Specify the detection interval (in hours) in which the number of malware detections must occur. Specify a number from **1** through **168**.
    - **Multiple malware detection** - This alert is generated if more than a specified number of malware types are detected over a specified number of hours on computers in the collection that you monitor. Specify the following information to configure this alert:

        - **Number of malware types detected:** The alert is generated when the specified number of different malware types are detected on computers in the collection. Specify a number from **2** through **32**.
        - **Interval for detection (hours):** Specify the detection interval, in hours, in which the number of malware detections must occur. Specify a number from **1** through **168**.
9. Click **OK** to close the *&lt;Collection Name&gt;***Properties** dialog box.

## Alert for outdated malware client

Beginning with Configuration Manager version 1702, you can configure an alert to ensure Endpoint Protection clients are not outdated. From any device collection, you can now add columns to the list for the following attributes **Antimalware Client Version** and **Endpoint Protection Deployment State**. For example, in the console navigate to **Assets and Compliance** &gt; **Overview** &gt; **Device Collections** &gt; **All Desktops and Server Clients**. Right-click the column header and select those columns to add. To check for an alert, view **Alerts** in the **Monitoring** workspace. If more than 20% of managed clients are running an expired version of antimalware software, the Antimalware client version is outdated alert is displayed. This alert doesn't appear on the **Monitoring** &gt; **Overview** tab. To update expired antimalware clients, enable software updates for antimalware clients.

To configure the percentage at which the alert is generated, expand **Monitoring** &gt; **Alerts** &gt; **All Alerts**, double-click **Antimalware clients out of date** and modify the **Raise alert if percentage of managed clients with an outdated version of the antimalware client is more than** option.

[Next step &gt;](endpoint-definition-updates)

[Back &gt;](endpoint-protection-site-role)