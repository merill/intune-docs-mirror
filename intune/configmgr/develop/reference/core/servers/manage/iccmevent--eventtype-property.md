---
layout: Conceptual
title: ICCMEvent::EventType Property - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property
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
description: ICcmEvent::EventType is a read/write property in Configuration Manager that indicates the type of Windows Management Instrumentation event that is being raised.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9d625eaa-f20e-e539-c556-8de674343141
document_version_independent_id: cbefa965-850e-b7ef-5481-07d1b043012c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 198e619d-bca5-016d-f45d-e7721782c4cf
---

# ICCMEvent::EventType Property - Configuration Manager | Microsoft Learn

`ICcmEvent::EventType` is a read/write property in Configuration Manager that indicates the type of Windows Management Instrumentation (WMI) event that is being raised.

## Syntax

```
[C++]
HRESULT ICcmEvent::EventType([out, retval] BSTR* sEventType);

HRESULT ICcmEvent::EventType([in] BSTR sEventType);
```

#### Parameters

`sEventType` Data type: `BSTR`

Qualifiers: [in, out, retval]

On input, the value to set for the event type. On output, this parameter points to the retrieved event type.

## Return Values

The property returns an `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

This property must correspond to an `ICcmEvent`-derived class registered in the root\ccm\events namespace.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).