---
layout: Conceptual
title: CCM_ServiceWindowManager Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class
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
description: Article detailing how to use CCM_ServiceWindowManager in Configuration Manager to manage service windows on the client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 80122e30-9f4b-9831-0d98-64267c6dd7c4
document_version_independent_id: 73cba832-d9f8-7ed3-7e74-e5211e040369
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a1fea4e3-c25f-b865-4d28-ab693a1c6cc0
---

# CCM_ServiceWindowManager Class - Configuration Manager | Microsoft Learn

The `CCM_ServiceWindowManager` WMI class is a client class, in Configuration Manager, manages service windows on the client computer.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_ServiceWindowManager();
```

## Methods

The following table shows the methods in the `CCM_ServiceWindowManager` class.

| Method | Description |
| --- | --- |
| [GetCurrentWindowAvailableTime Method in Class CCM_SoftwareUpdatesManager](getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager) | Gets the time remaining in a currently-active service window for a specified type. |
| [GetNextServiceWindowID Method in Class CCM_SoftwareUpdatesManager](getnextservicewindowid-method-in-class-ccm_servicewindowmanager) | Gets the identifier of the next service window closest to the current time. |
| [IsFutureWindowAvailable Method in Class CCM_SoftwareUpdatesManager](isfuturewindowavailable-method-in-class-ccm_servicewindowmanager) | Determines whether a service window of a specified type and a given duration is going to be available. |
| [IsWindowAvailableNow Method in Class CCM_SoftwareUpdatesManager](iswindowavailablenow-method-in-class-ccm_servicewindowmanager) | Determines whether a service window of a specified type and a given duration is available to run at the point of time when the call is made. |

## Properties

The `CCM_ServiceWindowManager` class does not define any properties.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).