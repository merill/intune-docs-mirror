---
layout: Conceptual
title: UpdateFeatureState Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/updatefeaturestate-method-in-class-sms_site
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
description: Learn how to update the enabled/disabled state of a feature using UpdateFeatureState WMI class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f97678df-8a78-add7-73dd-da674055fb97
document_version_independent_id: bb11c3a5-2f13-37b3-12d0-7bfe6662644c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/updatefeaturestate-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/updatefeaturestate-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/updatefeaturestate-method-in-class-sms_site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d2aad98d-ed96-d840-565c-6d4131ea309b
---

# UpdateFeatureState Method - Configuration Manager | Microsoft Learn

The `UpdateFeatureState` Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates the enabled/disabled state of a feature.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 UpdateFeatureState (
     String SiteCode,
     UInt32 FeatureID,
     Boolean IsEnabled
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: [in]

Site code of site to check. NULL indicates the current site.

`FeatureID` Data type: `UInt32`

Qualifiers: [in]

Feature identifier. Possible values are:

| Value | Feature identifier |
| --- | --- |
| 1 | SleepServer |

`IsEnabled` Data type: `Boolean`

Qualifiers: [in]

`true` if the feature is enabled.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).