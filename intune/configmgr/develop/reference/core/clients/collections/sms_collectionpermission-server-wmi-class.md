---
layout: Conceptual
title: SMS_CollectionPermission Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionpermission-server-wmi-class
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
description: Article outlining the use of SMS_CollectionPermission in Configuration Manager to query and define which collection scopes are associated to an RBAC role.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9767cf74-c56c-4734-2040-70d0fa148281
document_version_independent_id: 91544680-2621-7877-13b9-ec96de3a33d4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionpermission-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionpermission-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionpermission-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d7c26b12-f7ac-fcea-4f76-2149841ee3fa
---

# SMS_CollectionPermission Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionPermission` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, is used to query and define which collection scopes are associated to an RBAC role.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionPermission : SMS_BaseClass
{
      UInt32 AdminID;
      String CollectionID;
      String CollectionName;
      Boolean GrantedToCurrentUser;
      String LogonName;
      String RoleID;
      String RoleName;
};
```

## Methods

The `SMS_ CollectionPermission` class does not define any methods.

## Properties

`AdminID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The administrator id from RBAC, which is used to associate the collection between each instance of this class.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The ID that refers to the collection.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the collection.

`GrantedToCurrentUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

This value will be true if this permission is granted to the current user directly or indirectly (through a Security Group).

`LogonName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the resource.

`RoleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The role id from RBAC, which is used to associate the collection between each instance of this class.

`RoleName` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The name of the RBAC.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).