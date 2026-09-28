---
layout: Conceptual
title: SMS_PkgToPkgProgram_a Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pkgtopkgprogram_a-server-wmi-class
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
description: Learn how to relate an SMS Package Server Class with related objects with SMS_PkgToPkgProgram_a and the PackageID property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: aeec77a4-2b3b-23bc-bab6-b9b0d60e0f0b
document_version_independent_id: 05430af6-6b09-e9bb-b48c-eb43eaf8ff3c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_pkgtopkgprogram_a-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_pkgtopkgprogram_a-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_pkgtopkgprogram_a-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 49dc001e-4521-6313-71c5-1841081f41fe
---

# SMS_PkgToPkgProgram_a Class - Configuration Manager | Microsoft Learn

The `SMS_PkgToPkgProgram_a` association Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that uses the `PackageID` property to relate an [SMS_Package Server WMI Class](sms_package-server-wmi-class) object with related [SMS_Program Server WMI Class](sms_program-server-wmi-class) objects.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PkgToPkgProgram_a : SMS_BaseAssociation
{
     ref:SMS_Package package;
     ref:SMS_Program pkgProgram;
};
```

## Methods

The `SMS_PkgToPkgProgram_a` class does not define any methods.

## Properties

`package` Data type: `ref:SMS_Package`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Package Server WMI Class](sms_package-server-wmi-class) object path.

`pkgProgram` Data type: `ref:SMS_Program`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Program Server WMI Class](sms_program-server-wmi-class) object path.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).