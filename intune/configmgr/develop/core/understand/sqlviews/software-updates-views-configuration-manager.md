---
layout: Conceptual
title: Software updates views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/software-updates-views-configuration-manager
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
description: Information about the software updates metadata, software update groups, and software update bundles.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 018df616-2385-aa72-317d-4c1a7cf4293f
document_version_independent_id: 4515a892-d5ff-cc47-3cbf-c359825fe50c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/software-updates-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/software-updates-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/software-updates-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e6ffd767-0812-e98b-246a-4a54c7d2f05e
---

# Software updates views - Configuration Manager | Microsoft Learn

The Configuration Manager software updates views contain information about the software updates metadata, software update groups, software update bundles, and so on. Many of the status and status summarizer views provide information about software updates compliance, software update deployment evaluation and enforcement state, scan states, compliance status summarization, deployment status summarization, and so on. The compliance state for clients using an inventory scan tool, such as the Inventory Tool for Microsoft Updates, are picked up during the hardware inventory cycle and stored in the inventory views.

The following sections provide detailed information about software updates views, software updates status views, software updates status summarizer views, and software updates hardware inventory views.

## Software updates views

The software updates views contain information about software updates. When creating software updates reports for individual software updates or update bundles, the **v\_UpdateCIs** or **v\_UpdateInfo** views will most often be used in combination with other views. The software update views are described in this section.

### v\_AuthListInfo

Lists the software update groups, by CI\_ID, for the Configuration Manager hierarchy, including when the software update group was created, when it was last modified, who last modified the software update group, source site, title, description, and so on. This view contains a subset of information from the **v\_ConfigurationItems** view, joins the **v\_LocalizedCIProperties** view to retrieve software update group title and description information, and filters the information by **CIType**=9, which indicates an software update group configuration item. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, and **SDMPackage\_ID** columns.

### v\_EULAContent

Lists the license terms, by **EULAContentID** and **EULAContentUniqueID**, associated with software updates. The license terms text is in binary format. The view can be joined to the **v\_CIEULA\_LocalizedContent** view, which associates the software update (configuration item) to the license terms, by using the **EULAContentUniqueID** column.

### v\_ScannedUpdates

Lists all software updates, by **CI\_ID**, that have been scanned for software updates compliance on Configuration Manager clients, including Resource ID, scan time, and last local change time. The view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_SoftwareUpdateSource

Lists all sources for the software updates metadata, by **UpdateSource\_ID**, for the site. Configuration Manager sites should use **WSUS Enterprise Server** as the update source and **WUA** as the scan method. The view can be joined to the **v\_UpdateScanStatus** view by using the **UpdateSource\_ID** column.

### v\_UpdateCIs

Lists all of the software updates configuration items, by **CI\_ID** and **CI\_UniqueID**. The information in this view is a subset of information from the **v\_ConfigurationItems** view, retrieving all records where the configuration type is **Software Updates** or **Software Updates Bundle** (**CIType**=1 or 8), including article ID, bulletin ID, severity, date created, whether the update is deployed, and so on. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, and **SDMPackage\_ID** columns.

### v\_UpdateContents

Lists the software updates configuration items that have associated content, by CI\_ID, the configuration item ID for the software update in which the content is associated, the content ID, whether the content has been provisioned, the locale for the content, and so on. The configuration item ID for a software updates bundle is listed multiple times in the **CI\_ID** column, and the configuration item IDs for the software updates that are part of the bundle are listed in the **ContentCI\_ID** column. For example, a software update that is not a bundle would have the same configuration item ID in the **CI\_ID** and **ContentCI\_ID** columns. A software updates bundle would have one listing with the configuration item ID in the **CI\_ID** column and the same configuration item ID in the **ContentCI\_ID** columns, and then would have new listings containing the configuration item ID for the bundle in the **CI\_ID** column and the configuration item ID for the bundled software updates in the **ContentCI\_ID** column. The **ContentLevel** column represents how many times a configuration item ID is listed in the **ContentCI\_ID** column. The view can be joined to other views by using the **CI\_ID** and **Content\_ID** columns and to the **v\_CIContents\_All** view by using the **ContentCI\_ID** column.

### v\_UpdateInfo

Lists stand-alone software updates (CIType\_ID = 1) or software update groups (CIType\_ID = 9), by **CI\_ID**, and information about the update or bundle, such as configuration item type, configuration item version, data created, date last modified, whether the update or bundle has been deployed, associated bulletin ID, article ID, severity, and so on. Unlike the Configuration Manager console when it displays software updates, this view does not list the updates that are part of an update bundle. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, and **SDMPackage\_ID** columns.

## Software updates status views

The software updates status views provide information about software updates compliance, deployment evaluation, deployment enforcement, scan state, and so on. These views can generally be joined to other software updates and desired configuration management views by using the **CI\_ID** column. For more information about the status views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain software updates information are described in this section.

### v\_AssignmentState\_Combined

Lists the last state message received from Configuration Manager client computers for assigned software update deployments, including the assignment ID (deployment ID), resource ID, state type, and so on. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **StateType**, or **StateID** columns.

### v\_AssignmentStatePerTopic

Lists the last state message for each state type received from Configuration Manager client computers for assigned software update deployments, including assignment ID (deployment ID), resource ID, state type, and so on. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **TopicType**, and **StateID** columns.

### v\_UpdateAssignmentStatus

Lists the software update deployment assignments, the system resources that have been targeted, the last compliance state for the deployment, the last enforcement state for the deployments, the last evaluation state for the deployment, and so on. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **LastComplianceMessageID**, **LastEnforcementMessageID**, and **LastEvaluationMessageID** columns. The **LastComplianceMessageID** column provides the state ID for state messages with a topic type of 300. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 301. The **LastEvaluationMessageID** provides the state ID for state messages with a topic type of 302.

### v\_UpdateAssignmentStatus\_Live

Lists the software update deployments, the system resources that have been targeted, the last compliance state for the deployment, the last enforcement state for the deployments, the last evaluation state for the deployment, and so on. The **v\_UpdateAssignmentStatus\_Live** view contains a subset of information from the **v\_UpdateAssignmentStatus** view. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **LastComplianceMessageID**, **LastEnforcementMessageID**, and **LastEvaluationMessageID** columns. The **LastComplianceMessageID** column provides the state ID for state messages with a topic type of 300. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 301. The **LastEvaluationMessageID** provides the state ID for state messages with a topic type of 302.

### v\_Update\_ComplianceStatus

Lists the detection state for all software updates that have been scanned for compliance on Configuration Manager clients, as well as the resource ID of the client, last enforcement state ID, enforcement source, last status check time, and so on. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **Status**, and **LastEnforcementMessageID** columns. The Status column provides the state ID for state messages with a topic type of 500. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 402.

### v\_UpdateScanStatus

Lists the Configuration Manager client computers, by resource ID, that have scanned for software updates compliance and the last scan state, as well as the last scan time, last error code, last Windows Update Agent version, and so on. The view can be joined to other views by using the **ResourceID**, **UpdateSource\_ID**, and **LastScanState** columns.

Note

The **LastScanState** column provides the state ID for state messages with a topic type of 501.

### v\_UpdateState\_Combined

Lists the detection state for software updates that are not required on Configuration Manager client computers or the enforcement state for software updates that are required on Configuration Manager client computers, as well as the state ID, state time, enforcement source, and so on. The view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

Note

A value of 402 in the **StateType** column is for enforcement state, and a value of 500 is for compliance state.

## Software updates status summarizer views

The software updates status summarizers produce summaries from software updates state messages in the Configuration Manager site database. Status summaries are produced in real time as the summarizers receive state messages from Configuration Manager clients. The software updates status summarizer views provide summary information about software updates compliance, deployment evaluation, deployment enforcement, and scan state. For more information about the status summarizer views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The software update status views are described in this section.

### v\_AssignmentEnforcementSummaryPerUpdateAndState

Lists the software update deployments, by assignment ID, the software updates in the deployment, by **CI\_ID**, the enforcement state name, the count of Configuration Manager client computers that are in the enforcement state, and the total count of client computers that have been targeted for the deployment. The view can be joined to other views by using the **AssignmentID** and **CI\_ID** columns.

Note

The enforcement states listed in this view have a state type of 402.

### v\_Update\_ComplianceSummary

Lists all software updates, by **CI\_ID**, the last time summarization was run, the total count of client computers, the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states, and so on. The view can be joined to other views by using the **CI\_ID** column.

### v\_Update\_ComplianceSummary\_Live

Lists all software updates, by **CI\_ID**, the last time summarization was run, the total count of client computers, the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states, and so on. The view can be joined to other views by using the **CI\_ID** column.

### v\_Update\_DeploymentSummary\_Live

Lists all software updates, by **CI\_ID**, in active software update deployments, listed by AssignmentID, and summarized state reported by targeted clients. The view includes the target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states; the number of clients that have installed the software update or failed to install the update; and so on. The view can be joined to other views by using the **CI\_ID**, **AssignmentID**, and **CollectionID** columns.

### v\_UpdateDeploymentSummary

Lists all software updates, by **CI\_ID**, in software update deployments, listed by assignment ID, and summarized state reported by targeted clients. The view includes the target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states; the number of clients that have installed the software update or failed to install the update; and so on. The view can be joined to other views by using the **CI\_ID**, **AssignmentID**, and **CollectionID** columns.

Note

This view has been deprecated, no longer generates summary data, and may be removed in the future.

### v\_UpdateEnforcementSummaryPerCollection

Lists the summary state for all software updates that have been deployed. The view provides the software update, by **CI\_ID**, target collection, collection name, and summarized enforcement state reported by clients in the collection. The view can be joined to other views by using the **CI\_ID** column.

### v\_UpdateSummaryPerCollection

Lists the summary state for all software updates and the compliance state per collection. The view includes the software update, by **CI\_ID**; target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting not applicable, missing (required), present (already installed), and unknown states; and so on. The view can be joined to other views by using the **CI\_ID** and **CollectionID** columns.