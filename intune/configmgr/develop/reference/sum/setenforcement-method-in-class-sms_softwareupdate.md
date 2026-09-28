---
layout: Conceptual
title: SetEnforcement method in class SMS_SoftwareUpdate - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setenforcement-method-in-class-sms_softwareupdate
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how to set policy enforcement rules for software updates by editing the 'SetEnforcement' class method in the Configuration Manager.
locale: en-us
document_id: 911bd034-a0e9-2515-876d-ae6beae25b1a
document_version_independent_id: fa499811-6f00-cca8-6565-e84dc894e779
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/setenforcement-method-in-class-sms_softwareupdate.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/setenforcement-method-in-class-sms_softwareupdate
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/setenforcement-method-in-class-sms_softwareupdate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d4d103fb-099c-0206-c506-84c0829b0544
---

# SetEnforcement method in class SMS_SoftwareUpdate - Configuration Manager | Microsoft Learn

The `SetEnforcement` Windows Management Instrumentation (WMI) class method, in Configuration Manager, sets policy enforcement for the software update.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 SetEnforcement(
     Boolean Enforced,
     DateTime EffectiveDate
);
```

#### Parameters

`Enforced` Data type: `Boolean`

Qualifiers: [in]

`true` if policy enforcement is enabled for the configuration item.

`EffectiveDate` Data type: `DateTime`

Qualifiers: [in]

The date and time, in Coordinated Universal Time (UTC), when the configuration item is compliant.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).