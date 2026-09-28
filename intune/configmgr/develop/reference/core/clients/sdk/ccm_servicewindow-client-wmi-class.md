---
layout: Conceptual
title: CCM_ServiceWindow Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindow-client-wmi-class
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
description: Learn how to list instances of service windows in Configuration Manager using CCM_ServiceWindow class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2a2263f7-dd6b-f399-8850-8312847e9038
document_version_independent_id: 0411b2d9-24e7-77e8-a81d-f217829a0b56
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindow-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_servicewindow-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindow-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c8337e33-6e81-2b97-83ed-23f87ba05dfd
---

# CCM_ServiceWindow Class - Configuration Manager | Microsoft Learn

The `CCM_ServiceWindow` Client WMI class is a client class, in Configuration Manager, that lists instances of service windows.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_ServiceWindow
{
    UInt32 Duration;
    Datetime EndTime;
    String ID;
    Datetime StartTime;
    UInt32 Type;
};
```

## Methods

The `CCM_ServiceWindow` class does not define any methods.

## Properties

`Duration` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total duration, in seconds, of the service window.

`EndTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time to end the service window.

`ID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Service window identifier for this particular instance of service window.

`StartTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time to start the service window.

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Type of service window. The following table shows the list of possible values.

| Value | Service Window Type | Description |
| --- | --- | --- |
| 1 | ALLPROGRAM\_SERVICEWINDOW | All Deployment Service Window |
| 2 | PROGRAM\_SERVICEWINDOW | Program Service Window |
| 3 | REBOOTREQUIRED\_SERVICEWINDOW | Reboot Required Service Window |
| 4 | SOFTWAREUPDATE\_SERVICEWINDOW | Software Update Service Window |
| 5 | OSD\_SERVICEWINDOW | Task Sequences Service Window |
| 6 | USER\_DEFINED\_SERVICE\_WINDOW | Corresponds to non-working hours |

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).