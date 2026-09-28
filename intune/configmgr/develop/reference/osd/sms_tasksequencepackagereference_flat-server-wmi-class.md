---
layout: Conceptual
title: SMS_TaskSequencePackageReference_Flat Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference_flat-server-wmi-class
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
description: The SMS_TaskSequencePackageReference_Flat WMI class represents all classic package or application references for a task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e51898e8-74bf-1d5b-c4ed-58a6af1d85e5
document_version_independent_id: 6c04e599-02b6-a5ae-9899-3f8249c6bc90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference_flat-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequencepackagereference_flat-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference_flat-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7da6a6f2-0581-7cb1-b873-2b8f69f1d51f
---

# SMS_TaskSequencePackageReference_Flat Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequencePackageReference_Flat` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents all classic package or application references for a task sequence. The list also includes the applications that are dependent on the applications directly referenced in the task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequencePackageReference_Flat : SMS_BaseClass
{
    String Description;
    String Level;
    String ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String PackageID;
    String RefPackageID;
    String SourceID;
    UInt32 SourceSize;
    String Version;
};
```

## Methods

The `SMS_TaskSequencePackageReference_Flat` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

The description for the reference or dependent object.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

If the Task Sequence reference is to a legacy package, this property is the package identifier of the legacy package. If the Task Sequence reference is to an application, this property is the package identifier of the application.

`ObjectName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Display name for the reference or dependent object.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of reference or dependent object. Possible values are:

| Value | Object type |
| --- | --- |
| 0 | Classic Package |
| 3 | Driver Package |
| 5 | Software Update Package |
| 257 | Operating System Image Package |
| 258 | Boot Image Package |
| 259 | Operating System Installer Source Package |
| 512 | Application |

`Level` Data type: `String`

Access type: Read-only

Qualifiers: read

Reference or dependent object level in the dependency tree. For direct reference objects, this is 0.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

If the Task Sequence reference is to a legacy package, this property is the package identifier of the legacy package. If the Task Sequence reference is to an application, this property is the package identifier of the application.

`ObjectName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Display name for the reference or dependent object.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of reference or dependent object. Possible values are:

| Value | Object type |
| --- | --- |
| 0 | Classic Package |
| 3 | Driver Package |
| 5 | Software Update Package |
| 257 | Operating System Image Package |
| 258 | Boot Image Package |
| 259 | Operating System Installer Source Package |
| 512 | Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Package identifier of the task sequence.

`RefPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [none]

Reference or dependent object Package ID.

`SourceID` Data type: `String`

Access type: Read/Write

Qualifiers: [none]

Source object ID for dependency. For direct reference objects this s empty.

`SourceSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Package source size.

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: [none]

Reference or dependent object version.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).