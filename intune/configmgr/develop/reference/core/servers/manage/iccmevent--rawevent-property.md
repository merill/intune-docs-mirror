---
layout: Conceptual
title: ICCMEvent::RawEvent Property - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property
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
description: In Configuration Manager, ICcmEvent::RawEvent is a read-only property that indicates information to add to a raw event.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 86f1335a-ef90-62d6-5626-351dc3e871fa
document_version_independent_id: 34c037f6-ada9-4301-52c2-edf995c09d51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3c8b2612-44ab-c8fb-5865-7c840c30fe1b
---

# ICCMEvent::RawEvent Property - Configuration Manager | Microsoft Learn

`ICcmEvent::RawEvent` is a read-only property in Configuration Manager that indicates information to add to a raw event.

## Syntax

```
[C++]
HRESULT ICcmEvent::RawEvent([out, retval] IUnknown** ppWmiEvent);
```

#### Parameters

`ppWmiEvent` Data type: `IUnknown`

Qualifiers: [out, retval]

Pointer to a pointer to the `IUnknown` interface of the internal Windows Management Instrumentation (WMI) event.

## Return Values

The property returns an `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

Use of this property permits information that can't be added through the [SetProperty method](iccmevent--setproperty-method) method to be added to custom events.

This property is recommended only for advanced users who need to add information to custom events that can't be accomplished through the [SetProperty method](iccmevent--setproperty-method) method. It isn't supported in VBScript.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).