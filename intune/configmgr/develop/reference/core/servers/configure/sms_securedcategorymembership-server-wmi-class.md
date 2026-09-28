---
layout: Conceptual
title: SMS_SecuredCategoryMembership Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class
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
description: Learn how to use the SMS_SecuredCategoryMembership class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c75dcdfc-e4f8-53a6-6dad-c30115fcc337
document_version_independent_id: 10e72f0e-a2d0-e133-ca84-b8b30225f088
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: c2e5b7d6-0120-1cb0-1d71-da637867a2fd
---

# SMS_SecuredCategoryMembership Class - Configuration Manager | Microsoft Learn

The `SMS_SecuredCategoryMembership` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents object to security category assignment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SecuredCategoryMembership : SMS_BaseClass
{
    String CategoryID;
    String ObjectKey;
    UInt32 ObjectTypeID;
};
```

## Methods

The following table lists the methods in the `SMS_SecuredCategoryMembership` class.

| Method | Description |
| --- | --- |
| [AddMemberships Method in Class SMS_SecuredCategoryMembership](addmemberships-method-in-class-sms_securedcategorymembership) | Batch operation to assign objects to a security category. |
| [RemoveMemberships Method in Class SMS_SecuredCategoryMembership](removememberships-method-in-class-sms_securedcategorymembership) | Batch operation to remove objects from a security category |

## Properties

`CategoryID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The ID of security category.

`ObjectKey` Data type: `String`

Access type: Read/Write

Qualifiers: [key, sizelimit("256")]

The key of object.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The type id of the object. See the `SMS_RbacSecuredObject` class for details.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).