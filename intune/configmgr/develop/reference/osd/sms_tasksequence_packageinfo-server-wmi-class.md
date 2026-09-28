---
layout: Conceptual
title: SMS_TaskSequence_PackageInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_packageinfo-server-wmi-class
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
description: SMS_TaskSequence_PackageInfo WMI is an SMS provider server class that represents information about an operating system deployment task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bc4550a3-e076-e76b-10a9-1db671fbbb3f
document_version_independent_id: 8e160564-484e-69f3-af95-349899c1b6e3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_packageinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_packageinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_packageinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d23802ff-fc7f-73af-0e05-c213d0a0ee07
---

# SMS_TaskSequence_PackageInfo Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_PackageInfo` Windows Management Instrumentation (WMI) class is an SMS provider server class, in Configuration Manager, that represents information about an operating system deployment task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_PackageInfo
{
    String Name;
    String PackageId;
    UInt32 PkgType;
    UInt32 Size;
};

```

## Methods

The `SMS_TaskSequence_PackageInfo` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the package.

`PackageId` Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the package.

`PkgType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The package type.

`Size` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The size of the package, in kilobytes.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).