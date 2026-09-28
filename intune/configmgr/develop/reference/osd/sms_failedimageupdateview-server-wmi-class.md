---
layout: Conceptual
title: SMS_FailedImageUpdateView Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_failedimageupdateview-server-wmi-class
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
description: Learn how the SMS_FailedImageUpdateView Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents failed software update information in offline servicing image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f43f4981-cb5c-9e73-5b70-12d66de8ce6f
document_version_independent_id: 8cbae470-8323-1dcb-acda-7406a95d38f4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_failedimageupdateview-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_failedimageupdateview-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_failedimageupdateview-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e535d90-7944-ffc6-2290-d5f10ce70128
---

# SMS_FailedImageUpdateView Class - Configuration Manager | Microsoft Learn

The `SMS_FailedImageUpdateView` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents failed software update information in offline servicing image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_FailedImageUpdateView : SMS_BaseClass
{
    SInt32 FailedImageCount;
    String Title;
    SInt32 UpdateID;
};
```

## Methods

The `SMS_FailedImageUpdateView` class doesn't define any methods.

## Properties

`FailedImageCount` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Offline image count that failed to install this update.

`Title` Data type: `String`

Access type: Read/Write

Qualifiers: none

Software update display name.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

Software update local unique ID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).