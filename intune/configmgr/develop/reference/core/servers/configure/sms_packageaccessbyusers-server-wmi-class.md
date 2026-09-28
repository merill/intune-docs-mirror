---
layout: Conceptual
title: SMS_PackageAccessByUsers Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class
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
description: The SMS_PackageAccessByUsers WMI class is an SMS Provider server class, in Configuration Manager, that controls which users are granted access rights to a package folder or to distribution points.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bb765a0b-cca4-66fa-75cf-53b93ff20b87
document_version_independent_id: f335a5c4-e38c-3195-793a-c4e1ab013cb3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e4844696-4787-160b-cdde-7269aff1f622
---

# SMS_PackageAccessByUsers Class - Configuration Manager | Microsoft Learn

The `SMS_PackageAccessByUsers` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that controls which users are granted access rights to a package folder or to distribution points.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageAccessByUsers : SMS_BaseClass
{
      UInt32 Access;
      String PackageID;
      String UserName;
};
```

## Methods

The `SMS_PackageAccessByUsers` class doesn't define any methods.

## Properties

`Access` Data type: `UInt32`

Access type: Read/Write

Qualifiers:

[bits]

Access rights for the user. Possible values are listed below. The default value is 0x65.

| Value | Access right |
| --- | --- |
| 0 | READ |
| 1 | WRITE |
| 2 | EXECUTE |
| 3 | CREATE |
| 4 | DELETE |
| 5 | VIEW\_FOLDERS |
| 6 | VIEW\_FILES |
| 7 | CHANGE\_PERMISSIONS |
| 8 | CHANGE\_ATTRIBUTES |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID of the package to which the privileges apply. The default value is "".

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

User name or group name in the network abstraction layer (NAL) path format. The default value is "". For more information about the NAL path format, see `PackNALPath`.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

This class controls client access to package folders and distribution points by using Windows NT or Novell security.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).