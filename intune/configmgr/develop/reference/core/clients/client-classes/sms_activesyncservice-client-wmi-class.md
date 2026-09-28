---
layout: Conceptual
title: SMS_ActiveSyncService Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncservice-client-wmi-class
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
description: Learn how the SMS_ActiveSyncService class is a client Windows Management Instrumentation (WMI) class that represents the ActiveSync service on the client.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7304ba8c-487a-c757-f61b-189cceb9115b
document_version_independent_id: c9f4622b-4c26-2c02-38ed-90c9dbbad0b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncservice-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_activesyncservice-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncservice-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d84f2ab3-d405-b140-cc8c-47aa5545b641
---

# SMS_ActiveSyncService Class - Configuration Manager | Microsoft Learn

The `SMS_ActiveSyncService` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents the ActiveSync service on the client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ActiveSyncService : SMS_Class_Template
{
      String LastSyncTime;
      UInt32 MajorVersion;
      UInt32 MinorVersion;
};
```

## Methods

The `SMS_ActiveSyncService` class does not define any methods.

## Properties

`LastSyncTime` Data type: `String`

Access type: Read/Write

Qualifiers:

[SMS\_Report("True")]

The last time when the client was synchronized with connected devices.

`MajorVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The major version number of the client operating system.

`MinorVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The minor version number of the client operating system.

## Remarks

All properties of this class are marked with qualifiers to indicate that they represent items that are generated dynamically (reported) based on the content of the SMS\_def.mof file.