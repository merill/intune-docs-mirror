---
layout: Conceptual
title: Client deployment views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/client-deployment-views-configuration-manager
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
description: Views that contain information about the deployment state of Configuration Manager client computers and devices.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 82c5103f-bd01-f8ce-7d01-bbe651da827c
document_version_independent_id: 89040e73-81cd-e453-8e83-2a7ef5ae2757
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/client-deployment-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/client-deployment-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/client-deployment-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: a6e26a42-5c1a-3de2-8f49-d6dce8459d8a
---

# Client deployment views - Configuration Manager | Microsoft Learn

There are no primary client deployment views, but there are status views that contain information about the deployment state of Configuration Manager client computers and devices. For more information about the status views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain client deployment information are described in this section.

## Client deployment views

### v\_ClientDeploymentState

Lists all Configuration Manager clients, by SMSID, and the last client deployment state reported, as well as the fully qualified domain name (FQDN), NetBIOS name, assigned site code, client version, and so on.

The view can be joined to other views by using the **SMSID**, **FQDN**, **NetBiosName**, and **LastMessageStateID** columns.

- **LastMessageStateID**: The state ID for topic type 800.
- **DeploymentBeginTime**: The last message time when the message's state ID is STATE\_STATEID\_CLIENT\_DEPLOYMENT\_STARTED (100), telling the server that the deployment starts. It clears the DeploymentEndTime time.
- **DeploymentEndTime**: The last message time when the state ID is STATE\_STATEID\_CLIENT\_DEPLOYMENT\_SUCCEEDED (400) or STATE\_STATEID\_CLIENT\_DEPLOYMENT\_SUCCEEDED\_REBOOT\_SUCCEEDED (401). This tells the server that the deployment ends.
- **AssignmentBeginTime**: The time when getting state ID STATE\_STATEID\_CLIENT\_ASSIGNMENT\_STARTED (500).
- **AssignmentEndTime**: The time that the assignment was done with ID STATE\_STATEID\_CLIENT\_ASSIGNMENT\_SUCCEEDED (700).
- The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_DeviceClientDeploymentState

Lists all Configuration Manager mobile device clients that are enrolled by Configuration Manager, by device client ID, NetBIOS name, and device ID, and the last device deployment state reported, as well as the assigned site code, device client version, and so on. This status view is also listed and described in [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager).

The view can be joined to other views by using the **DeviceClientID**, **DeviceNetBiosName**, and **DeviceDeploymentState** columns. The **DeviceDeploymentState** column contains the state ID for topic type 800. The **DeviceClientID** column contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_CombinedDeviceResources

Lists information about all devices in the Configuration Manager site, by machine ID. The columns in this view display information such as the client name, GUID, operating system, assigned site code, domain, the client version and whether the device is a virtual machine. This view can be joined to other views by using the **MachineID** column.

### v\_CP\_Machine

Lists information about client push attempts to install the client on computers. Includes the computer name, when the last attempt to install the client occurred, the assigned site code, the number of attempts made, and the current status. This view can be joined to other views by using the **MachineID** column.

## Client notification views

Client notification in Configuration Manager lets some client operations be performed as soon as possible, instead of during the usual client policy polling interval. For example, you can use the client management task **Download Computer Policy** to instruct computers to download policy as soon as possible. Additionally, you can start some actions for Endpoint Protection, such as a malware scan of a client.

The client notification views are described in this section.

### v\_BGB\_ResTask

List information about the tasks performed on devices by Configuration Manager client notification. This view can be joined to other views by using the **ResourceID** column.

### v\_BGB\_ResTaskPush

Lists information about the tasks deployed by Configuration Manager client notification, including the task ID, deployment ID, and status. This view can be joined to other views by using the **ResourceID** column.

### v\_BGB\_Task

Lists information about all tasks that have been deployed by client notification. This includes the task ID, when the task was created and whether it has expired. This view can be joined to other views by using the **TaskID** column.

### v\_BgbMP

List the server name and database IDs of the management points that send out client notifications. This view can be joined to other views by using the **ServerName** column.

### v\_BgbServerCurrent

Lists status information about online and offline clients for each server that sends client notification requests. This view can be joined to other views by using the **ServerID** column.

### v\_ClientAction

Lists information about client notification actions that were taken. This information appears in the **Client Operations** node of the Configuration Manager console. This view can be joined to other views by using the **ID** column.

### v\_ClientActionImportance

Lists information about the priority of client notification tasks as shown in the **Client Operations** node of the Configuration Manager console. This view can be joined to other views by using the **ClientOperationID** column.

### v\_ClientActionResult

Lists information about the results of client notification actions that are shown in the **Client Operations** node of the Configuration Manager console. This view can be joined to other views by using the **MachineID** column.

### v\_ClientOperationInProcessing

Lists the ID number of client notification operations that are currently being processed. It is unlikely that this view will be joined to other views.

### v\_ClientOperationLinkedObjects

Lists information about objects that are linked to client notification actions. It is unlikely that this view will be joined to other views.

### v\_ClientOperationTargets

Lists information about the computers on which client notification actions took place. This view can be joined to other views by using the **MachineID** column.