---
layout: Conceptual
title: AddChangeNotification method in class SMS_DeviceSettingPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/addchangenotification-method-in-class-sms_devicesettingpackage
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
description: Learn how to use Configuration Manager AddChangeNotification Windows Management Instrumentation (WMI) class method to add a device setting package change notification.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e9a2dd78-1f9b-6dbc-6ee0-3c9360e530b8
document_version_independent_id: ba8168fd-5761-4e5f-ed20-4a1b40101454
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/addchangenotification-method-in-class-sms_devicesettingpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/addchangenotification-method-in-class-sms_devicesettingpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/addchangenotification-method-in-class-sms_devicesettingpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5a2ce3fc-31aa-dfe7-dc3f-7f831c64386b
---

# AddChangeNotification method in class SMS_DeviceSettingPackage - Configuration Manager | Microsoft Learn

The `AddChangeNotification` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds a device setting package change notification.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddChangeNotification();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements