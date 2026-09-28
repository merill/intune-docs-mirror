---
layout: Conceptual
title: SMS_EndpointProtectionThreatData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_endpointprotectionthreatdata-server-wmi-class
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
description: An SMS Provider server class that represents Microsoft official threats. It's a metadata table and all data is extracted from the signature update.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 53101b51-e405-90ee-0478-8ee5fa0ffd21
document_version_independent_id: 410dc058-0106-dad8-171f-7182e7ee86f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_endpointprotectionthreatdata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_endpointprotectionthreatdata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_endpointprotectionthreatdata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fc684d19-93c0-d77d-fbf1-13b24c9be834
---

# SMS_EndpointProtectionThreatData Class - Configuration Manager | Microsoft Learn

The `SMS_EndpointProtectionThreatData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft official threats. This is a metadata table/view and all data is extracted from the signature update.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_EndpointProtectionThreatData : SMS_BaseClass
{
    UInt32 DefaultActionID;
    UInt32 IsAV;
    String Name;
    UInt64 ThreatID;
    UInt32 VersionFirstUpdated;
};
```

## Methods

The `SMS_EndpointProtectionThreatData` class doesn't define any methods.

## Properties

`DefaultActionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier of the action the EndPoint Protection agent takes for this particular threat.

| Value | Default action |
| --- | --- |
| 0 | Recommend |
| 2 | Quarantine |
| 3 | Remove |
| 6 | Allow |

`IsAV` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Is Antimalware or Antispyware.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Threat name.

`ThreatID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

Threat identifier.

`VersionFirstUpdated` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Signature version.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).