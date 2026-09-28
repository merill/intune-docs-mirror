---
layout: Conceptual
title: SMS_TaskSequencePackageReference Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents a Configuration Manager application or package in the task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c99743cd-e0d4-cca2-163d-db7191120784
document_version_independent_id: b61313b5-80e4-cedd-f7f0-deef83e4dcb7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequencepackagereference-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e227cf5-b27d-c98b-ae05-ad953f56b72e
---

# SMS_TaskSequencePackageReference Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequencePackageReference` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager application or package in the task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequencePackageReference : SMS_BaseClass
{
    String Description;
    String ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String PackageID;
    String Version;
};
```

## Methods

The `SMS_TaskSequencePackageReference` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object description.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Reference object ID.

`ObjectName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object name.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Reference object type.

| Value | Object type |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 5 | PKG\_TYPE\_SWUPDATES |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Task sequence package ID.

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object version.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).