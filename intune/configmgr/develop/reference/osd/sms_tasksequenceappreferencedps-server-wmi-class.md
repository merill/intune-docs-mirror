---
layout: Conceptual
title: SMS_TaskSequenceAppReferenceDps Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencedps-server-wmi-class
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
description: An SMS Provider server class that represents a distribution point to which a Configuration Manager application in the task sequence is distributed.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 53c8152c-2014-4ad7-e17f-14c26f1c10fd
document_version_independent_id: 422a93c4-3792-bb17-e674-7ec469dffebe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencedps-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequenceappreferencedps-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencedps-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 344e0de1-f6de-a022-b0fb-6c428dd4e8ec
---

# SMS_TaskSequenceAppReferenceDps Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequenceAppReferenceDps` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a distribution point to which a Configuration Manager application in the task sequence is distributed.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceAppReferenceDps :
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

The `SMS_TaskSequenceAppReferenceDps` class does not define any methods.

## Properties

`Hash` Data type: `String`

Access type: Read/Write

Qualifiers: none

Hash for application.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package ID for application.

`ServerNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

NALPath for distribution point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Site code for distribution point.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Source version for application.

`TaskSequenceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID for task sequence package.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).