---
layout: Conceptual
title: SMS_AdminCategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_admincategory-server-wmi-class
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
description: Learn how to represent an association between the admin account and an RBA secured category in Configuration Manager using SMS_AdminCategory.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 987f5433-3ec5-4786-9698-061dab2c2ee7
document_version_independent_id: 565398db-e0bf-fc39-933a-9c5a4f5ef953
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_admincategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_admincategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_admincategory-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 3aefe64c-28e2-eb15-e648-e9d177c4c73d
---

# SMS_AdminCategory Class - Configuration Manager | Microsoft Learn

The `SMS_AdminCategory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an association between the admin account and an RBA secured category.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AdminCategory : SMS_BaseClass
{
    UInt32 AdminID;
    String CategoryID;
};
```

## Methods

The `SMS_AdminCategory` class does not define any methods.

## Properties

`AdminID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the associated account.

`CategoryID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID of the associated RBA secured category.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).