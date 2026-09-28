---
layout: Conceptual
title: SMS_TopThreatPath Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_topthreatpath-server-wmi-class
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
description: The SMS_ThreatPath Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents summarizes the threats path found in 7 days per collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 666def69-5e0d-cf31-0b71-0902b5f8aa06
document_version_independent_id: 8d4a9c1e-3905-cb06-005c-fee32fcf536e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_topthreatpath-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_topthreatpath-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_topthreatpath-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1bdd0ead-52b2-82dc-58c8-36e4436594f9
---

# SMS_TopThreatPath Class - Configuration Manager | Microsoft Learn

The `SMS_ThreatPath` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents summarizes the threats path found in 7 days per collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ThreatPath : SMS_BaseClass
{
    String CollectionID;
    UInt32 DuplicateCount;
    String Path;
    UInt64 ResourceID;
    UInt64 ThreatID;
    String ThreatName;
    UInt32 TotalCount;
};
```

## Methods

The `SMS_ThreatPath` class doesn't define any methods.

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifier of the collection.

`DuplicateCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of members with a threat in that path.

`Path` Data type: `String`

Access type: Read/Write

Qualifiers: none

Path of the threat.

`ResourceID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

Identifier of the resource.

`ThreatID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Identifier of the threat.

`ThreatName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the threat.

`TotalCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Total count of members in the collection.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).