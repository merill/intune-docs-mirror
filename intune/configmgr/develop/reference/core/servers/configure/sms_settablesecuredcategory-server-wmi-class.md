---
layout: Conceptual
title: SMS_SettableSecuredCategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_settablesecuredcategory-server-wmi-class
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
description: Article outlining the use of SMS_SettableSecuredCategory class to assign secured categories to select objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 45499e59-8ee8-c728-9350-ead28f20be93
document_version_independent_id: ea3929c0-a6c2-9818-90af-d8066c000a2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_settablesecuredcategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_settablesecuredcategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_settablesecuredcategory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36051666-3e04-a751-3cf5-3c1ecc4d618d
---

# SMS_SettableSecuredCategory Class - Configuration Manager | Microsoft Learn

The `SMS_SettableSecuredCategory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the list of secured categories which the current user can assign to certain types of objects.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SettableSecuredCategory : SMS_BaseClass
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

The `SMS_SettableSecuredCategory` class does not define any methods.

## Properties

`CategoryDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read, sizelimit("512")]

Description of the security category.

`CategoryID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

ID of the security category.

`CategoryName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit("256")]

Name of the security category.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The name of the user who created the security category.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when the security category was created.

`IsBuiltIn` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if this is a built-in security category (All or Default).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The name of the user who last modified the security category.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when the security category was last modified.

`NumberOfAdmins` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of admin accounts associated with this security category.

`NumberOfObjects` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of objects associated with this security category.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

The object type which the current user has permission to assign to this security category.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("3")]

Site where this was security category was created.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).