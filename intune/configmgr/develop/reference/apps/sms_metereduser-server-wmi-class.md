---
layout: Conceptual
title: SMS_MeteredUser Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_metereduser-server-wmi-class
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
description: Learn how to list users that have used metered applications in Configuration Manager with SMS_MeteredUser.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 43f11810-4ee0-33ce-c742-aaee661bb440
document_version_independent_id: 37abf37e-3836-df3a-51a5-f6bf8372d2c8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_metereduser-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_metereduser-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_metereduser-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a3e68e6-4d49-3170-fa91-af82b019dbc1
---

# SMS_MeteredUser Class - Configuration Manager | Microsoft Learn

The `SMS_MeteredUser` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists users that have used metered applications.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MeteredUser : SMS_BaseClass
{
      String Domain;
      String FullName;
      UInt32 MeteredUserID;
      String UserName;
};
```

## Methods

The `SMS_MeteredUser` class does not define any methods.

## Properties

`Domain` Data type: `String`

Access type: Read/Write

Qualifiers: None

Domain to which the metered user belongs.

`FullName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Fully qualified domain name of the user in domain\user format.

`MeteredUserID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID for the metered user.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the metered user.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class is the source for the `MeteredUserID` foreign key used in other classes.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).