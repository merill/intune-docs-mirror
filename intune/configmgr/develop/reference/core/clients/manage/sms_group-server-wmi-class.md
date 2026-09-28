---
layout: Conceptual
title: SMS_Group Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class
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
description: Learn how to represent a resource group that serves as the abstract base class for SMS_G_System Server WMI Class using SMS_Group class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5176652e-4189-28e7-3a87-acffd15c793f
document_version_independent_id: 7524d28d-926e-6fd5-57eb-f02482ed1237
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0272aef5-4be2-4259-203f-c78a545224af
---

# SMS_Group Class - Configuration Manager | Microsoft Learn

The `SMS_Group` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a resource group and serves as the abstract base class for [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Group : SMS_BaseClass
{
     UInt32 ResourceID;
};
```

## Methods

The `SMS_Group` class does not define any methods.

## Properties

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Configuration Manager-supplied ID that uniquely identifies a client resource. The default value is 0. This ID is unique only for the site.

Inventory items with the same `ResourceID` property are all found on the same client.

## Remarks

Class qualifiers for this class include:

- Abstract
- Read:ToSubClass

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).