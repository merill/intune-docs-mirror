---
layout: Conceptual
title: SMS_AIHardwareRequirements Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aihardwarerequirements-server-wmi-class
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
description: Learn how to associate a software title with hardware requirements using SMS_AIHardwareRequirements in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c77283c5-a031-a5bb-911c-12589e514d9a
document_version_independent_id: da306597-758b-fde5-cf1b-8cd75609b5a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aihardwarerequirements-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/sms_aihardwarerequirements-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aihardwarerequirements-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 21be2d46-7fb9-eaff-9502-d8e5d49082f4
---

# SMS_AIHardwareRequirements Class - Configuration Manager | Microsoft Learn

The `SMS_AIHardwareRequirements` Windows Management Instrumentation (WMI) class, in Configuration Manager, associates a software title with hardware requirements.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AIHardwareRequirements : SMS_BaseClass
{
      boolean IsLocal;
      uint32 MinCPU;
      sint64 MinDiskFree;
      sint64 MinDiskSize;
      sint64 MinRAM;
      string Product;
      uint32 State;
};
```

## Methods

The following table lists the methods in the `SMS_AIHardwareRequirements` class.

| Method | Description |
| --- | --- |
| [GetSummary Method in Class SMS_AIHardwareRequirements](getsummary-method-in-class-sms_aihardwarerequirements) | Retrieves a summary of all class instances based on the State property of the class. |

## Properties

`IsLocal` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` when this entry has been created locally. Local entries are editable.

`MinCPU` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Minimum CPU in megahertz.

`MinDiskFree` Data type: `SInt64`

Access type: Read/Write

Qualifiers: None

Minimum free disk space in KB.

`MinDiskSize` Data type: `SInt64`

Access type: Read/Write

Qualifiers: None

Minimum total disk size in KB.

`MinRAM` Data type: `SInt64`

Access type: Read/Write

Qualifiers: None

Minimum total RAM in KB.

`Product` Data type: `String`

Access type: Read/Write

Qualifiers: key

The software title.

`State` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

| Value | Description |
| --- | --- |
| 0 | Validated, defined by Microsoft through System Center Online. |
| 1 | User-defined. |

## Remarks

Class qualifiers for this class include:

- DisplayName("AI Hardware Requirements")
- Dynamic
- Provider("ExtnProv")
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).