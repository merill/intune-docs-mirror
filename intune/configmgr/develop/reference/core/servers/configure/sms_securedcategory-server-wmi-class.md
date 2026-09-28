---
layout: Conceptual
title: SMS_SecuredCategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class
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
description: The SMS_SecuredCategory Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents the RBA security category.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0b1b22f8-78bf-2ea7-a58a-c696629a1bdc
document_version_independent_id: e45bd6aa-ce50-d21f-73a6-2cad69872ace
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2240c661-1426-3931-b0dd-4812a0a57910
---

# SMS_SecuredCategory Class - Configuration Manager | Microsoft Learn

The `SMS_SecuredCategory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the RBA security category. An RBA security category defines a set of objects associated with it.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SecuredCategory : SMS_BaseClass
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
    String SourceSite;
};
```

## Methods

The `SMS_SecuredCategory` class does not define any methods.

## Properties

`CategoryDescription` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("512")]

Description of the RBA security category.

`CategoryID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

The ID of the RBA security category. Auto generated when the RBA security category is created.

`CategoryName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, sizelimit("256"]

Name of the RBA security category.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The logon name of the user that created the RBA security category.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when the RBA security category was created.

`IsBuiltIn` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if RBA security category is built-in.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

User that last modified the RBA security category.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Time when the RBA security category was last modified.

`NumberOfAdmins` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of admin accounts associated with the RBA security category.

`NumberOfObjects` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of objects associated with the RBA security category.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("3")]

The site where the RBA security category was created.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).