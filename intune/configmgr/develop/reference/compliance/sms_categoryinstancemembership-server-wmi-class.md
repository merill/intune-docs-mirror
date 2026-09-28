---
layout: Conceptual
title: SMS_CategoryInstanceMembership Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancemembership-server-wmi-class
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
description: The `SMS_CategoryInstanceMembership` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, which represents the relationship between categories and configuration item objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1f460c0c-4399-cd29-aa86-073871d3dd75
document_version_independent_id: f75f5659-28da-2da0-b4b3-c85289b8ae9d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_categoryinstancemembership-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_categoryinstancemembership-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_categoryinstancemembership-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 41ceb242-1ad2-a175-4e34-b6bf2f0e9f37
---

# SMS_CategoryInstanceMembership Class - Configuration Manager | Microsoft Learn

The `SMS_CategoryInstanceMembership` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, which represents the relationship between categories and configuration item objects.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CategoryInstanceMembership
{
    UInt32 CategoryInstanceID;
    String ObjectKey;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_CategoryInstanceMembership` class does not define any methods.

## Properties

`CategoryInstanceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

[SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class)

`ObjectKey` Data type: `String`

Access type: Read/Write

Qualifiers: [key, sizelimit]

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

[SMS_ObjectContentInfo Server WMI Class](../core/servers/console/sms_objectcontentinfo-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).