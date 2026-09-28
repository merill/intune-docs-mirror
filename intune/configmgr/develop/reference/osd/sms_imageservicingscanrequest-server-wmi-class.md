---
layout: Conceptual
title: SMS_ImageServicingScanRequest Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageservicingscanrequest-server-wmi-class
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
description: The SMS_ImageServicingScanRequest WMI class is an SMS Provider class that represents scan request for offline servicing image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e417912c-f7c3-3d9e-d4af-26e0a032eb51
document_version_independent_id: 53d9b439-c4d8-7f92-57f1-90da2d5e3bd3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_imageservicingscanrequest-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_imageservicingscanrequest-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_imageservicingscanrequest-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8acb2e63-f6ff-40bf-fc9b-51dff4550be5
---

# SMS_ImageServicingScanRequest Class - Configuration Manager | Microsoft Learn

The `SMS_ImageServicingScanRequest` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents scan request for offline servicing image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageServicingScanRequest : SMS_BaseClass
{
    String ImagePackageID;
    DateTime LastRunDateTime;
    SInt32 Status;
};
```

## Methods

The `SMS_ImageServicingScanRequest` class does not define any methods.

## Properties

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID for offline servicing image that is installed on client computer.

`LastRunDateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last run time for this offline image.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Status for this offline image installation

| Value | Installation status |
| --- | --- |
| 1 | Success |
| 2 | Failed |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).