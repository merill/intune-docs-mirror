---
layout: Conceptual
title: SMS_BoundaryGroupRelationships Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class
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
description: Learn how to represent the fallback relationships for boundary groups in Configuration Manager using SMS_BoundaryGroupRelationships.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 53078ebf-56f8-d058-0c8d-62be42e35bba
document_version_independent_id: c2b94361-07fb-714a-003f-6f8873eb966c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 276c060e-f1b3-9b8d-2254-1a3a87d2071a
---

# SMS_BoundaryGroupRelationships Class - Configuration Manager | Microsoft Learn

The `SMS_BoundaryGroupRelationships` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents fallback relationships for boundary groups.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupRelationships : SMS_BaseClass
{
    UInt32 DestinationGroupID;
    String DestinationGroupName;
    UInt32 SourceGroupID;
    String SourceGroupName;
};
```

## Methods

The following table shows the methods in `SMS_BoundaryGroupRelationships`.

| Method | Description |
| --- | --- |
| [FallbackDP Method in Class SMS_BoundaryGroupRelationships](fallbackdp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a distribution point (DP). |
| [FallbackMP Method in Class SMS_BoundaryGroupRelationships](fallbackmp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a management point (MP). |
| [FallbackSMP Method in Class SMS_BoundaryGroupRelationships](fallbacksmp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a state migration point (SMP). |
| [FallbackSUP Method in Class SMS_BoundaryGroupRelationships](fallbacksup-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a software update point (SUP). |

## Properties

`DestinationGroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the destination boundary group.

`DestinationGroupName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the destination boundary group.

`SourceGroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the source boundary group.

`SourceGroupName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the source boundary group.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).