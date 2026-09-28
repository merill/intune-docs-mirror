---
layout: Conceptual
title: SMS_TaskSequenceReferencesInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencereferencesinfo-server-wmi-class
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
description: The SMS_TaskSequenceReferencesInfo class associates a task sequence with its package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: aec00222-85a2-0612-e8cd-9b78357f8cc3
document_version_independent_id: 709e0e6f-bc89-cc13-7e0b-7ae268db4865
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequencereferencesinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequencereferencesinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequencereferencesinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 56016725-2f53-06c3-a1ac-109aa1ac8f7c
---

# SMS_TaskSequenceReferencesInfo Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequenceReferencesInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that associates a task sequence with its package.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceReferencesInfo : SMS_BaseClass
{
      String PackageID;
      String ProgramName;
      String ReferenceDescription;
      String ReferenceName;
      String ReferencePackageID;
      UInt32 ReferencePackageType;
      String ReferenceProgramName;
      String ReferenceVersion;
};
```

## Methods

The `SMS_TaskSequenceReferencesInfo` class does not define any methods.

## Properties

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID of the task sequence package.

`ProgramName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the program associated with the task sequence.

`ReferenceDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

The long description of the reference package.

`ReferenceName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the reference package.

`ReferencePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: None

ID of the reference package.

`ReferencePackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of the reference package. Possible values are:

| Value | Package type |
| --- | --- |
| 0 (0x0000) | PKG\_TYPE\_REGULAR |
| 3 (0x0003) | PKG\_TYPE\_DRIVER |
| 4 (0x0004) | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 (0x0005) | PKG\_TYPE\_SWUPDATES |
| 257 (0x0101) | PKG\_TYPE\_IMAGE |
| 258 0x0102) | PKG\_TYPE\_BOOTIMAGE |
| 259 (0x0101) | PKG\_TYPE\_OSINSTALLIMAGE |

`ReferenceProgramName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the reference program for the task sequence.

`ReferenceVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The version of the reference package.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).