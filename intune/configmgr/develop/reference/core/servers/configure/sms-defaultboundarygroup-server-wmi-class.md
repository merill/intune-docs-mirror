---
layout: Conceptual
title: SMS_DefaultBoundaryGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms-defaultboundarygroup-server-wmi-class
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
description: Learn how to represent a default boundary group using SMS_DefaultBoundaryGroup Windows Management Instrumentation (WMI) class.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e4ef511e-e26a-bf80-f8b2-836b4434032f
document_version_independent_id: 5cac2eb3-1e1d-f7aa-341a-d29342f2e551
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms-defaultboundarygroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms-defaultboundarygroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms-defaultboundarygroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bff457e0-836c-ef83-30d3-837479f0799c
---

# SMS_DefaultBoundaryGroup Class - Configuration Manager | Microsoft Learn

The `SMS_DefaultBoundaryGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a default boundary group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DefaultBoundaryGroup : SMS_BaseClass
{
    String CreatedBy;
    DateTime CreatedOn;
    String DefaultSiteCode;
    String Description;
    UInt32 GroupID;
    UInt32 MemberCount;
    String ModifiedBy;
    DateTime ModifiedOn;
    String Name;
    Boolean Shared;
    UInt32 SiteSystemCount;
};
```

## Methods

The following table shows the methods in `SMS_DefaultBoundaryGroup`.

| Method | Description |
| --- | --- |
| [AddBoundary Method in Class SMS_DefaultBoundaryGroup](addboundary-method-in-class-sms-defaultboundarygroup) | Adds one or more boundaries to a default boundary group. |
| [AddSiteSystem Method in Class SMS_DefaultBoundaryGroup](addsitesystem-method-in-class-sms-defaultboundarygroup) | Adds one or more site system servers to a default boundary group. |
| [RemoveBoundary Method in Class SMS_DefaultBoundaryGroup](removeboundary-method-in-class-sms-defaultboundarygroup) | Removes one or more boundaries from a default boundary group. |
| [RemoveSiteSystem Method in Class SMS_DefaultBoundaryGroup](removesitesystem-method-in-class-sms-defaultboundarygroup) | Removes one or more site system servers from a default boundary group. |

## Properties

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who created the default boundary group.

`CreatedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time that the default boundary group was created.

`DefaultSiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read, SizeLimit("3")]

The site code to which new clients will be automatically assigned.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: [read]

A description for the boundary group.

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

An automatically-generated unique ID for the boundary group.

`MemberCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of members in the boundary group. The default value is 0.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User who modified the boundary group.

`ModifiedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time that the boundary group was modified.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read, unique, not\_null]

Name of the boundary group.

`Shared` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Indicates whether the boundary group was created by Migration Manager for a shared distribution point.

`SiteSystemCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of site system servers that are associated with the boundary group. The default value is 0.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).