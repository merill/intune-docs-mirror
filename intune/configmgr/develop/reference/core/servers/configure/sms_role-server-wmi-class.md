---
layout: Conceptual
title: SMS_Role Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class
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
description: Learn how the SMS_Role Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an RBA role.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4884adf9-90f1-d78c-3b31-23ed419d4094
document_version_independent_id: bb62c0a8-123d-36bb-d5d8-4141829f21fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_role-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 43317f9d-c163-7869-f91d-dbaa4a148650
---

# SMS_Role Class - Configuration Manager | Microsoft Learn

The `SMS_Role` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an RBA role.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Role : SMS_BaseClass
{
    String CopiedFromID;
    String CreatedBy;
    DateTime CreatedDate;
    Boolean IsBuiltIn;
    Boolean IsSecAdminRole;
    String LastModifiedBy;
    DateTime LastModifiedDate;
    UInt32 NumberOfAdmins;
    SMS_ARoleOperation Operations[];
    String RoleDescription;
    String RoleID;
    String RoleName;
    String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_Role` class.

| Method | Description |
| --- | --- |
| [ExportRole Method in Class SMS_Role](exportrole-method-in-class-sms_role) | Exports roles to an XML string. |
| [ImportRole Method in Class SMS_Role](importrole-method-in-class-sms_role) | Imports a role defined by an XML string to the database. |

## Properties

`CopiedFromID` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("8")]

Role ID from which this role was copied.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

Name of the user that created this role.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date that the role was created.

`IsBuiltIn` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if this is a built-in role.

`IsSecAdminRole` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

`true`, if this role as a secured admin role. The role is security admin role if the role has can create or modify admin permission.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The name of the user that last modified the role.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The time when the role was last modified.

`NumberOfAdmins` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of admin accounts associated with this role.

`Operations` Data type: `SMS_ARoleOperation` Array

Access type: Read/Write

Qualifiers: [lazy]

The operations granted to this role.

`RoleDescription` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("512")]

Description of the role.

`RoleID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

The ID of the role. Auto generated when the role was created. This ID will not change during the lifetime of the role and will be unique across sites.

`RoleName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, sizelimit("256")]

Name of the role.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("3")]

The site code of the site where the role was created.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).