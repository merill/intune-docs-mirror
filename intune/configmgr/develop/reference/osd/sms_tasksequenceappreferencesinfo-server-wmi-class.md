---
layout: Conceptual
title: SMS_TaskSequenceAppReferencesInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencesinfo-server-wmi-class
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
description: Learn how to represent a Configuration Manager application in the task sequence using SMS_TaskSequenceAppReferencesInfo class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6cfefda0-9f35-272e-01d2-eb21a3c324d5
document_version_independent_id: 86ce94f0-987c-be3c-e19c-d331723564c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencesinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequenceappreferencesinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencesinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 06cca09f-7507-eb55-5139-f93981df5870
---

# SMS_TaskSequenceAppReferencesInfo Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequenceAppReferencesInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager application in the task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceAppReferencesInfo : SMS_BaseClass
{
    String PackageID;
    SInt32 RefAppCI_ID;
    String RefAppModelName;
    String RefAppPackageID;
};
```

## Methods

The `SMS_TaskSequenceAppReferencesInfo` class does not define any methods.

## Properties

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Package ID of the task sequence.

`RefAppCI_ID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

CI\_ID of the referenced by task sequence application.

`RefAppModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The model name of the referenced by task sequence application.

`RefAppPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package ID of the referenced by task sequence application.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).