---
layout: Conceptual
title: SMS_CIRelation_Flat Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_cirelation_flat-server-wmi-class
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
description: The SMS_CIRelation_Flat Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a flat list of relationship information for directly or indirectly related configuration items.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f5a57529-6dfd-9124-4ccd-8435dc85317e
document_version_independent_id: 9ef49a8c-d1b3-20de-ae10-dcbbdd967f84
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_cirelation_flat-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_cirelation_flat-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_cirelation_flat-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 251c0187-c054-0c55-8c86-43c11196013e
---

# SMS_CIRelation_Flat Class - Configuration Manager | Microsoft Learn

The `SMS_CIRelation_Flat` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a flat list of relationship information for directly or indirectly related configuration items.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIRelation_Flat : SMS_BaseClass
{
    UInt32 FromCIID;
    Boolean IsVersionSpecific;
    UInt32 Level;
    UInt32 RelationType;
    UInt32 ToCIID;
};
```

## Methods

The `SMS_CIRelation_Flat` class does not define any methods.

## Properties

`FromCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

[SMS_CIRelation Server WMI Class](../sum/sms_cirelation-server-wmi-class)

`IsVersionSpecific` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

[SMS_CIRelation Server WMI Class](../sum/sms_cirelation-server-wmi-class)

`Level` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Level represents the depth of the relationships between configuration items. A direct relationship to the configuration item is 1 and an indirect relationship can be 2 or higher.

`RelationType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

[SMS_CIRelation Server WMI Class](../sum/sms_cirelation-server-wmi-class)

`ToCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

[SMS_CIRelation Server WMI Class](../sum/sms_cirelation-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).