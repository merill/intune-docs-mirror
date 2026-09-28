---
layout: Conceptual
title: SMS_Admin server WMI class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_admin-server-wmi-class
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
description: Details of the SMS_Admin server WMI class
ms.date: 2020-09-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c5eb6f85-f198-9376-41f0-659fdedb744e
document_version_independent_id: 4ac9de95-cf78-41e6-4d8e-3ed22e2f798a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_admin-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_admin-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_admin-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d479ff3f-41d7-9300-3932-d10d30fc7629
---

# SMS_Admin server WMI class - Configuration Manager | Microsoft Learn

The `SMS_Admin` WMI class is an SMS provider server class in Configuration Manager that represents the role-based administration (RBA) user.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Admin : SMS_BaseClass
{
    UInt32 AccountType;
    UInt32 AdminID;
    String AdminSid;
    String Categories[];
    String CategoryNames[];
    String CollectionNames[];
    String CreatedBy;
    DateTime CreatedDate;
    String DisplayName;
    String DistinguishedName;
    SMS_AdminExtendedData ExtendedData[];
    Boolean IsCovered;
    Boolean IsDeleted;
    Boolean IsGroup;
    String LastModifiedBy;
    DateTime LastModifiedDate;
    String LogonName;
    SMS_APermission Permissions[];
    String RoleNames[];
    String Roles[];
    String SKey;
    String SourceSite;
};
```

## Methods

The `SMS_Admin` class includes the following methods:

- [GetAdminExtendedData method in class SMS_Admin](getadminextendeddata-method-in-class-sms_admin): Returns extended data the current user and its groups have for a given type.

## Properties

`AccountType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The type of account. The possible values are:

| Value | Account type |
| --- | --- |
| 0 | User |
| 1 | Group |
| 2 | Machine |
| 128 | UnverifiedUser |
| 129 | UnverifiedGroup |
| 130 | UnverifiedMachine |

`AdminID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

The ID of the admin object. This value is auto-generated when the object is created and never changed afterward. The default value is 0.

`AdminSid` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy, not\_null, unique]

The SID of the user, when the admin is created.

`Categories` Data type: `String` Array

Access type: Read-only

Qualifiers: [lazy, read]

The RBA secured categories associated with this account.

`CategoryNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

The name of the RBA secured categories associated with this account.

`CollectionNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

The name of the collections associated with this account.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The name of the user that created this account.

`CreatedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date when this account was created.

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit ("512")]

The display name of the account.

`DistinguishedName` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("4000")]

The distinguished name of the account. If the distinguished name is not null, `LogonName` and `AdminSid` will be ignored.

`ExtendedData` Data type: `SMS_AdminExtendedData` Array

Access type: Read/Write

Qualifiers: [lazy]

Reserved for internal use.

`IsCovered` Data type: `Boolean`

Access type: Read-only

Qualifiers: [lazy, read]

`true` if the current user has more permissions than this account.

`IsDeleted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if the account has been deleted from Active Directory.

`IsGroup` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true`, if the account is an Active Directory security group.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, SizeLimit("512")]

The name of the user that last modified this account.

`LastModifiedDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The date the account was last modified.

`LogonName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, sizelimit]

The logon name of the account. This could be a Windows NT 4 name (ADS\_NAME\_TYPE\_NT4) or a simple domain name (ADS\_NAME\_TYPE\_DOMAIN\_SIMPLE).

`Permissions` Data type: `SMS_APermission` Array

Access type: Read/Write

Qualifiers: [lazy]

The list of permission assigned to this account.

`RoleNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

The list of role names associated with the current user.

The following table lists the built-in role identifiers and names:

| Role identifier | Role name |
| --- | --- |
| SMS0001R | Full Administrator |
| SMS0002R | Read-only Analyst |
| SMS0003R | Remote Tools Operator |
| SMS0004R | Asset Manager |
| SMS0006R | Compliance Settings Manager |
| SMS0007R | Application Deployment Manager |
| SMS0008R | Application Author |
| SMS0009R | Application Administrator |
| SMS000AR | Operating System Deployment Manager |
| SMS000BR | Infrastructure Manager |
| SMS000CR | Software Update Manager |
| SMS000ER | Operations Administrator |
| SMS000FR | Security Administrator |
| SMS000GR | EndPoint Protection Manager |
| SMS000HR | Company Resource Access Manager |

`Roles` Data type: `String` Array

Access type: Read-only

Qualifiers: [lazy, read]

The ID of roles associated with the current user.

For a list of the the built-in role identifiers and names, see the `RoleNames` property.

`SKey` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Reserved for internal use.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, sizelimit("3")]

The site where the account was created.

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).