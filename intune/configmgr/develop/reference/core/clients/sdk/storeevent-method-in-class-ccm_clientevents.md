---
layout: Conceptual
title: StoreEvent Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/storeevent-method-in-class-ccm_clientevents
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
description: The StoreEvent Windows Management Instrumentation class method generates store events.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5ca226d1-d4f6-cb75-b1f3-c89a35d7d1ce
document_version_independent_id: 05adfb78-4c78-fbef-ad18-911f6e96ac66
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/storeevent-method-in-class-ccm_clientevents.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/storeevent-method-in-class-ccm_clientevents
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/storeevent-method-in-class-ccm_clientevents.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a2a0471d-5388-e09a-bc92-48f1d4e5b990
---

# StoreEvent Method - Configuration Manager | Microsoft Learn

The `StoreEvent` Windows Management Instrumentation (WMI) class method generates store events.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```

 uint32 StoreEvent
{
     UInt32 DurationMS,
     String ComponentName,
     String EventName,
     String SessionId
 };

```

## Parameters

`DurationMS` Data type: `UInt32`

Qualifiers: [in]

The duration of the event in milliseconds.

`ComponentName` Data type: `String`

Qualifiers: [in]

The name of the component.

`EventName` Data type: `String`

Qualifiers: [in]

The name of the event.

`SessionId` Data type: `String`

Qualifiers: [in]

The ID of the session.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).