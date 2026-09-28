---
layout: Conceptual
title: SMS_AssociatedSecuredCategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_associatedsecuredcategory-server-wmi-class
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
description: The SMS_AssociatedSecuredCategory WMI class is an SMS Provider server class, in Configuration Manager, that represents the list of RBA security categories associated with the current admin user.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 78691339-5601-7708-5267-b636846f467b
document_version_independent_id: 5ffa99b1-9425-01c6-c877-dad03c1ae59e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_associatedsecuredcategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_associatedsecuredcategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_associatedsecuredcategory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 033c142c-0e1d-5cc4-5e11-534a4b3f88c0
---

# SMS_AssociatedSecuredCategory Class - Configuration Manager | Microsoft Learn

The `SMS_AssociatedSecuredCategory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the list of RBA security categories associated with the current admin user.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AssociatedSecuredCategory : SMS_BaseClass
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

The `SMS_AssociatedSecuredCategory` class does not define any methods.

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

The user who created the RBA security category.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when the RBA security category was created.

`IsBuiltIn` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if this is a built-in RBA security category (All or Default).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The user who last modified this RBA security category.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when this RBA security category was last modified.

`NumberOfAdmins` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of RBA admins associated with this RBA security category.

`NumberOfObjects` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of objects associated with this RBA security category.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

The object type of the object which the current user can assign to this RBA security category.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("3")]

The source site of the RBA security category.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).