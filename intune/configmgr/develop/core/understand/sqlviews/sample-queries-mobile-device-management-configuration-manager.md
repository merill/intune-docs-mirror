---
layout: Conceptual
title: Sample queries for mobile device management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-mobile-device-management-configuration-manager
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
description: Sample queries that show how to join mobile device management views to other views when the device is managed by Configuration Manager.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c273e1d4-453b-3574-8cc8-4642c6c8f7a8
document_version_independent_id: 2c4f5fbf-dc32-c9f3-471e-175b8c9d3506
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-mobile-device-management-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-mobile-device-management-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-mobile-device-management-configuration-manager.md
cmProducts: []
platformId: 47495226-e639-e10f-5546-55e057ea760f
---

# Sample queries for mobile device management - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join mobile device management views to other views when the device is managed by Configuration Manager. Mobile device management views will most often be joined to other views by using the **ResourceID** and **DeviceClientID** columns.

## Joining mobile device management hardware inventory and discovery views

The following query retrieves all mobile device Configuration Manager clients, by NetBIOS name, the operating system, the amount of storage space on the device, and the amount of free storage space on the device. The results are sorted by the NetBIOS name. The query joins the **v\_GS\_DEVICE\_COMPUTER\_SYSTEM** mobile device management hardware inventory view with the **v\_R\_System** discovery view by using the **ResourceID** column, and it joins the **v\_GS\_DEVICE\_COMPUTER\_SYSTEM** and **v\_GS\_DEVICE\_MEMORY** mobile device management hardware inventory views by using the **ResourceID** column.

```sql
    SELECT v_R_System.Netbios_Name0, 
    ��v_R_System.Operating_System_Name_and0, 
    ��v_GS_DEVICE_MEMORY.Storage0, 
    ��v_GS_DEVICE_MEMORY.StorageFree0 
    FROM v_GS_DEVICE_COMPUTER_SYSTEM INNER JOIN v_R_System ON 
    ��v_GS_DEVICE_COMPUTER_SYSTEM.ResourceID = v_R_System.ResourceID 
    ��INNER JOIN v_GS_DEVICE_MEMORY ON 
    ��v_GS_DEVICE_COMPUTER_SYSTEM.ResourceID = v_GS_DEVICE_MEMORY.ResourceID 
    ORDER BY v_R_System.Netbios_Name0 
```

## Joining mobile device management and status views

The following query retrieves the deployment state for all mobile device Configuration Manager clients, including the state name and description, NetBIOS name for the device, IP address, assigned site code, and deployment date and time. The results are sorted by the deployment state and then the NetBIOS name. The query joins the **v\_DeviceClientDeploymentState** mobile device management view with the **v\_StateNames** status view by using the **StateID** column. The retrieved information is filtered by the topic type of 800, which includes state messages for client deployment.

```sql
    SELECT v_StateNames.StateName AS [Deployment State], 
    ��v_StateNames.StateDescription AS Description, 
    ��v_DeviceClientDeploymentState.DeviceNetBiosName AS [Device Name], 
    ��v_DeviceClientDeploymentState.IPAddress AS [IP Address], 
    ��v_DeviceClientDeploymentState.AssignedSiteCode AS [Assigned Site], 
    ��v_DeviceClientDeploymentState.DeviceDeploymentTime AS [Time Deployed] 
    FROM v_DeviceClientDeploymentState INNER JOIN v_StateNames ON 
    ��v_DeviceClientDeploymentState.DeviceDeploymentState = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 800) 
    ORDER BY [Deployment State], [Device Name] 
```