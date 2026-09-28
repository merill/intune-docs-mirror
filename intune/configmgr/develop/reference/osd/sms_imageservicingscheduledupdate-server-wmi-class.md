---
layout: Conceptual
title: SMS_ImageServicingScheduledUpdate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageservicingscheduledupdate-server-wmi-class
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
description: The SMS_ImageServicingScheduledUpdate WMI class is an SMS Provider server class that represents all schedules for one software update in offline servicing image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a12c9b56-5b47-258b-1c3c-3050f3ca9fd3
document_version_independent_id: 672694a4-0bb2-77bb-2e2d-0275cbc4a691
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_imageservicingscheduledupdate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_imageservicingscheduledupdate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_imageservicingscheduledupdate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 74130262-3c4a-3fcc-73a8-92cc9b72c587
---

# SMS_ImageServicingScheduledUpdate Class - Configuration Manager | Microsoft Learn

The `SMS_ImageServicingScheduledUpdate` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents all schedules for one software update in offline servicing image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageServicingScheduledUpdate : SMS_BaseClass
{
    SInt32 ScheduleID;
    SInt32 UpdateID;
};
```

## Methods

The `SMS_ImageServicingScheduledUpdate` class does not define any methods.

## Properties

`ScheduleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

ID for software update installation schedule.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

ID for software update in offline servicing image.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).