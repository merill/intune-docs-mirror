---
layout: Conceptual
title: SMS_TaskSequenceReferenceDps Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencereferencedps-server-wmi-class
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
description: Learn about the simplified syntax, methods, properties, and requirements of the SMS_TaskSequenceReferenceDps server class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b89745d5-99ed-b89f-4744-8cc6ab850759
document_version_independent_id: b3befa4a-adeb-7de2-b414-6d577f87902f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequencereferencedps-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequencereferencedps-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequencereferencedps-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dab692bd-54eb-0653-0b49-e9776024cad9
---

# SMS_TaskSequenceReferenceDps Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequenceReferenceDps` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the package that is available for the task sequence at a specified distribution point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceReferenceDps
{
      String Hash;
      String PackageID;
      String ServerNALPath;
      String SiteCode;
      UInt32 SourceVersion;
      String TaskSequenceID;
};
```

## Methods

The `SMS_TaskSequenceReferenceDps` class does not define any methods.

## Properties

`Hash` Data type: `String`

Access type: Read/Write

Qualifiers: None

A hash of package content.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the package associated with the task sequence.

`ServerNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

The server network abstraction layer (NAL) path to the package at a particular distribution point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code for the distribution point.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The version of the package source.

`TaskSequenceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The ID for the task sequence.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).