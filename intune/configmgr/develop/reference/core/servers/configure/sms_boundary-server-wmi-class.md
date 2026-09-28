---
layout: Conceptual
title: SMS_Boundary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundary-server-wmi-class
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
description: An SMS Provider server class that represents a boundary defined within the hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6992c6c7-098f-ad9b-98a7-06215b1f120d
document_version_independent_id: 25473048-2b44-ea48-3200-c022906a7585
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_boundary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_boundary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_boundary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4ea24686-4830-933e-1d13-1acfe6ad7991
---

# SMS_Boundary Class - Configuration Manager | Microsoft Learn

The `SMS_Boundary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a boundary defined within the hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Boundary : SMS_BaseClass
{
    UInt32 BoundaryFlags;
    UInt32 BoundaryID;
    UInt32 BoundaryType;
    String CreatedBy;
    DateTime CreatedOn;
    String DefaultSiteCode[];
    String DisplayName;
    UInt32 GroupCount;
    String ModifiedBy;
    DateTime ModifiedOn;
    String SiteSystems[];
    String Value;
};
```

## Methods

The `SMS_Boundary` class does not define any methods.

## Properties

`BoundaryFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This property is obsolete, use the `Flags` property in `SMS_BoundaryGroupSiteSystems` instead.

Specifies the connection type of the boundary. Possible values are:

| Value | Connection type |
| --- | --- |
| 0 | FAST |
| 1 | SLOW |

`BoundaryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique identifier of the boundary.

`BoundaryType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Boundary type.

| Value | Boundary type |
| --- | --- |
| 0 | IPSUBNET |
| 1 | ADSITE |
| 2 | IPV6PREFIX |
| 3 | IPRANGE |

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User that created the boundary.

`CreatedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the boundary was created.

`DefaultSiteCode` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

Site code new clients will be auto assigned to.

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Display name of the boundary.

`GroupCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of boundary groups that have this boundary.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User that last modified the boundary.

`ModifiedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the boundary was last modified.

`SiteSystems` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

Site system machines within the boundary.

`Value` Data type: `String`

Access type: Read/Write

Qualifiers: none

Boundary value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).