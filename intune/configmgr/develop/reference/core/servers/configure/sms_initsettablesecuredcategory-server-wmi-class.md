---
layout: Conceptual
title: SMS_InitSettableSecuredCategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_initsettablesecuredcategory-server-wmi-class
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
description: In Configuration Manager, the SMS_InitSettableSecuredCategory Windows Management Instrumentation class is an SMS Provider server class that represents the list of RBA security categories.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7dc77a28-5d00-2e5f-aafb-ef7a3780317d
document_version_independent_id: 959c386b-e57c-0b74-c2ad-734f4a163f9b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_initsettablesecuredcategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_initsettablesecuredcategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_initsettablesecuredcategory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a5e1bce0-a015-3bef-f8d9-a0f36d8a61a2
---

# SMS_InitSettableSecuredCategory Class - Configuration Manager | Microsoft Learn

The `SMS_InitSettableSecuredCategory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the list of RBA security categories.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InitSettableSecuredCategory : SMS_BaseClass
{
    String CategoryDescription;
    String CategoryID;
    String CategoryName;
    String CreatedBy;
    DateTime CreatedDate;
    Boolean IsBuiltIn;
    String LastModifiedBy;
    DateTime LastModifiedDate;
    UInt32 NumberOfAdmins;
    UInt32 NumberOfObjects;
    UInt32 ObjectTypeID;
    String SourceSite;
};
```

## Methods

The `SMS_InitSettableSecuredCategory` class does not define any methods.

## Properties

`CategoryDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read, sizelimit("512")]

Description of the RBA security category.

`CategoryID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

ID of the RBA security category.

`CategoryName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit("256")]

Name of the RBA security category.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

Name of the user who created the RBA security category.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date the RBA security category was created.

`IsBuiltIn` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if this RBA security category is built-in (All or Default).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

User who last modified this RBA security category.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Time this RBA security category was last modified.

`NumberOfAdmins` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of admin accounts associated with this RBA security category.

`NumberOfObjects` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of objects associated with this RBA security category.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Object type which the current user has permissions to assign to this RBA security category.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("3")]

Site where the RBA security category was created.

## Remarks

Current user can assign objects to the RBA security categories specified by this class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).