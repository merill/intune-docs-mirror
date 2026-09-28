---
layout: Conceptual
title: GetFeatures Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getfeatures-method-in-class-sms_whatsnewfeature
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
description: This article describes the Get Features Method in Class SMS_WhatsNewFeature. The syntax is detailed below.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 65f76739-218f-820d-31bb-0d252e4afaf0
document_version_independent_id: 580495a1-84f5-876a-5ec7-1f9a7e550116
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/getfeatures-method-in-class-sms_whatsnewfeature.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/getfeatures-method-in-class-sms_whatsnewfeature
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/getfeatures-method-in-class-sms_whatsnewfeature.md
cmProducts: []
platformId: fba5bac6-64ee-ae9d-e451-1ee7ee54d1b2
---

# GetFeatures Method - Configuration Manager | Microsoft Learn

For internal use only.

## Syntax

```
SInt32 GetFeatures(
     UInt32 MinMilestone,
     UInt32 MaxMilestone,
     UInt32 LocaleID,
     SMS_WhatsNewFeature Features[]
);

```

#### Parameters

`MinMilestone` Data type: `UInt32`

Qualifiers: [in]

Reserved for internal use.

`MaxMilestone` Data type: `UInt32`

Qualifiers: [in]

Reserved for internal use.

`LocaleID` Data type: `UInt32`

Qualifiers: [in]

Reserved for internal use.

`Features` Data type: `SMS_WhatsNewFeature Array`

Qualifiers: [out]

Reserved for internal use.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).