---
layout: Conceptual
title: SMS_SiteControlDaySchedule Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontroldayschedule-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents usage information for each hour of the day.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 96afb01d-f8e6-2eef-6d95-157a59d9677d
document_version_independent_id: 65b4f94f-b42a-55f6-7bd5-89a84fd313c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontroldayschedule-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sitecontroldayschedule-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sitecontroldayschedule-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f9f1053f-fb5a-ce65-de32-92cea7a126e8
---

# SMS_SiteControlDaySchedule Class - Configuration Manager | Microsoft Learn

The `SMS_SiteControlDaySchedule` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents usage information for each hour of the day.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteControlDaySchedule
{
     Boolean Backup[24];
     UInt32 HourUsage[24];
     Boolean update;
};
```

## Methods

The `SMS_SiteControlDaySchedule` class does not define any methods.

## Properties

`Backup` Data type: `Boolean` Array

Access type: Read/Write

Qualifiers: None

Array containing 24 elements, one for each hour of the day. A value of `true` indicates that the address (sender) embedding `SMS_SiteControlDaySchedule` can be used as a backup.

`HourUsage` Data type: `UInt32` Array

Access type: Read/Write

Array containing 24 elements, one for each hour of the day. This property specifies the type of usage for each hour. Possible values are:

| Value | Usage type |
| --- | --- |
| 1 | ALL\_PRIORITY |
| 2 | ALL\_BUT\_LOW |
| 3 | HIGH\_ONLY |
| 4 | CLOSED |

`update` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the usage data is saved when the parent address object is saved.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).