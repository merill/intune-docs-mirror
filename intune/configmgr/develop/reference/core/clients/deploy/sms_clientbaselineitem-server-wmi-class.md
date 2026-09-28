---
layout: Conceptual
title: SMS_ClientBaselineItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselineitem-server-wmi-class
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
description: In Configuration Manager, the SMS_ClientBaselineItem WMI class is an SMS Provider server class that represents a client deployment baseline item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 11d1f698-6b65-e546-454c-c54593f1f3f2
document_version_independent_id: 937a80eb-ce5e-0126-a553-82d01d464c2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselineitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientbaselineitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselineitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8437294b-beaf-1ea5-2454-9f842c342389
---

# SMS_ClientBaselineItem Class - Configuration Manager | Microsoft Learn

The `SMS_ClientBaselineItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment baseline item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientBaselineItem: SMS_BaseClass
{
    UInt32 BaselineFlags;
    UInt32 BaselineItemID;
    String Name;
    UInt32 Platform;
    UInt32 Type;
    String UniqueID;
};

```

## Methods

The `SMS_ClientBaselineItem` class does not define any methods.

## Properties

`BaselineFlags` Data type: `UInt32`

Access type: Read

Qualifiers: none

Baseline flags to indicate which baseline this item belongs to.

`BaselineItemID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

Client baseline item ID.

`Name` Data type: `String`

Access type: Read

Qualifiers: none

Client baseline item name.

`Platform` Data type: `UInt32`

Access type: Read

Qualifiers: none

The platform of the client baseline item. Possible values are:

| Value | Platform |
| --- | --- |
| 1 | x86 |
| 2 | x64 |

`Type` Data type: `UInt32`

Access type: Read

Qualifiers: none

The client baseline item type. Possible values are:

| Value | Baseline item type |
| --- | --- |
| 1 | Patch or CU |
| 2 | Language Pack |

`UniqueID` Data type: `String`

Access type: Read

Qualifiers: none

The GUID of the client baseline item.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).