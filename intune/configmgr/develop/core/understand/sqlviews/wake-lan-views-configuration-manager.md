---
layout: Conceptual
title: Wake On LAN views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/wake-lan-views-configuration-manager
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
description: Information about the objects that have Wake On LAN enabled.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 671e90a8-de5d-89ee-9f57-ec289efaec6c
document_version_independent_id: 88ec6b7a-ba82-6058-f4e3-cfd0e1892fa9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/wake-lan-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/wake-lan-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/wake-lan-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 1b999730-f75c-9291-4f25-fad616c5b13f
---

# Wake On LAN views - Configuration Manager | Microsoft Learn

The Configuration�Manager Wake On LAN views contain information about the objects, such as application management, software updates, and task sequence deployments, that have Wake On LAN enabled, as well as the clients that are Wake On LAN enabled, and clients that have deployments that are Wake On LAN enabled. There is also a status view that contains information about the Wake On LAN error messages that have been reported. Most often, the Wake On LAN views will be joined to discovery views by using the **ResourceID** column, and to application management and compliance settings views by using the **ObjectID** column.

The following sections provide detailed information about Wake On LAN views and the Wake On LAN status view.

## Wake On LAN views

The Wake On LAN views are described in this section.

### v\_WOLClientTimeZones

Lists the time zone offsets for all Wake On LAN�enabled clients. It is unlikely that this view will be joined with other views.

### v\_WOLCommunicationHistory

Lists the Wake On LAN communication history, including the message description, time of the communication, status message attribute, and so on. The **BatchID**, **ObjectType**, and **ID** columns contain status message attributes, such as a deployment ID or unique configuration item ID. The view can be joined to other views by using the **BatchID**, **ObjectType**, and **ID** columns.

### v\_WOLEnabledAdvertisements

Lists the software deployments, by name and advertisement ID that have Wake On LAN enabled. The **ObjectType** value for software deployment is **1**, the **ObjectName** column contains the name of the advertisement, and the **ObjectID** column contains the advertisement ID of the advertisement. The view can be joined to other views by using the **ObjectID** column.

### v\_WOLEnabledAssignments

Lists the software update deployments, by name and unique deployment ID that have Wake On LAN enabled. The **ObjectType** value for software updates is 2, the **ObjectName** column contains the name of the deployment, and the **ObjectID** column contains the unique assignment ID of the deployment. The view can be joined to other views by using the **ObjectID** column.

### v\_WOLEnabledObjects

Lists the objects, by name and object ID, that have Wake On LAN enabled, as well as the object type. For example, a software update deployment that has Wake On LAN enabled will be listed with an **ObjectType=2**, the deployment name will be listed in the **ObjectName** column, and the assignment unique ID will be listed in the **ObjectID** column. The view can be joined to other views by using the **ObjectID** column and to the **v\_WOLGetSupportedObjects** view by using the **ObjectType** column.

### v\_WOLEnabledTaskSequences

Lists the task sequence advertisements, by object type, name and ID that have Wake On LAN enabled. The **ObjectType** value for task sequence is 3, the **ObjectName** column contains the name of the task sequence advertisement, and the **ObjectID** column contains the advertisement ID of the task sequence advertisement. The view can be joined to other views by using the **ObjectID** column.

### v\_WOLGetPendingObjectSchedules

Lists the objects, by the object ID that are scheduled for mandatory assignment, including the object type, target collection, schedule, and so on. The view can be joined to other views by using the **Object** column, which is the same as the **ObjectID** columns in other Wake On LAN views, and to the **v\_WOLGetSupportedObjects** view by using the **ObjectType** column.

### v\_WOLGetSupportedObjects

Lists the Wake On LAN object types, by object type and object name. For example, object type 1 is for software distribution, object type 2 is for software updates, and object type 3 is for task sequence. The view can be joined to other Wake On LAN views by using the **ObjectType** column.

### v\_WOLGetWOLEnabledSites

Lists the sites where Wake On LAN is enabled, by site code and site server name. It is unlikely that this view will be joined with other views.

### v\_WOLSUMTargetedClients

Lists the Configuration Manager clients, by **ResourceID**, where a software deployment that has Wake On LAN enabled targets the client. The object type, object ID (unique assignment ID of the deployment), assigned site, and current time zone are also listed. The view can be joined to other views by using the **ResourceID** and **ObjectID** columns.

### v\_WOLSWDistTargetedClients

Lists the Configuration Manager clients, by **ResourceID**, where a software deployment that has Wake On LAN enabled targets the client. The object type, object ID (advertisement ID of the deployment), assigned site, and current time zone are also listed. The view can be joined to other views by using the **ResourceID** and **ObjectID** columns.

### v\_WOLTargetedClients

Lists the Configuration Manager clients, by ResourceID, where an object that has Wake On LAN enabled targets the client, such as a software deployment, software update, or task sequence deployment. The object type, object ID, assigned site, and current time zone are also listed. The view can be joined to other views by using the **ResourceID** and **ObjectID** columns, and to the **v\_WOLGetSupportedObjects** view by using the **ObjectType** column.

### v\_WOLTSTargetedClients

Lists the Configuration Manager clients, by **ResourceID**, where a task sequence deployment that has Wake On LAN enabled targets the client. The object type, object ID (advertisement ID of the task sequence deployment), assigned site, and current time zone are also listed. The view can be joined to other views by using the **ResourceID** and **ObjectID** columns.

### v\_WOLWorkstationInfo

Lists all Wake On LAN�enabled clients, by **ResourceID** and **MachineName**, the assigned site, and the current time zone. The view can be joined to other views by using the **ResourceID** column.

## Wake On LAN status views

The Wake On LAN status view contains information about the Wake On LAN error messages. For more information about the status views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The status view that contains Wake On LAN information is described in this section.

### v\_WOLCommunicationErrorStatus

Lists the Wake On LAN error status messages that have been reported, including message description and time of the error. The **BatchID**, **ObjectType**, and **ID** columns contain status message attributes, such as an advertisement ID or unique configuration item ID. The view can be joined to other views by using the **BatchID**, **ObjectType**, and **ID** columns.