---
layout: Conceptual
title: SMS_ImageUpdateStatusView Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageupdatestatusview-server-wmi-class
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
description: The SMS_ImageUpdateStatusView WMI class represents software update information that is used by offline servicing image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 873b5860-17fd-a600-93b7-f2c6ac93bfb1
document_version_independent_id: 4bec63e9-5f52-cc35-7ff5-aa7de257ae97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_imageupdatestatusview-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_imageupdatestatusview-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_imageupdatestatusview-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3e86d4f4-b148-e295-eb48-b02d2262ddd1
---

# SMS_ImageUpdateStatusView Class - Configuration Manager | Microsoft Learn

The `SMS_ImageUpdateStatusView` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents software update information that is used by offline servicing image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageUpdateStatusView : SMS_BaseClass
{
    SInt32 ErrorCode;
    SInt32 ImageIndex;
    String ImagePackageID;
    String PackageDescription;
    String PackageName;
    SInt32 UpdateID;
};
```

## Methods

The `SMS_ImageUpdateStatusView` class does not define any methods.

## Properties

`ErrorCode` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Error code for software update installation.

`ImageIndex` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

Index for offline servicing image.

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID for offline servicing image.

`PackageDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for offline servicing image.

`PackageName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name for offline servicing image.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

ID for software update.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).