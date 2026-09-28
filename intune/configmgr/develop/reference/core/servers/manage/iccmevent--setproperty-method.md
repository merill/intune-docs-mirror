---
layout: Conceptual
title: ICCMEvent::SetProperty Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method
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
description: Learn how to set an event property in Configuration Manager using ICcmEvent::SetProperty method class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 180b69e8-3055-dbce-dfb0-46d1d90034b5
document_version_independent_id: 9fd07d1a-10e8-fc0e-af1d-1f3a44bc78d5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b32e712e-4a89-0c7c-f3b2-38603af1da98
---

# ICCMEvent::SetProperty Method - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ICcmEvent::SetProperty` method sets an event property.

## Syntax

```
[C++]
HRESULT ICcmEvent::SetProperty
(
      BSTR sPropName,
   VARIANT* vPropValue
);
```

#### Parameters

`sPropName` Data type: `BSTR`

Qualifiers: [in]

Name of the property to set. This must correspond to a property name in the Windows Management Instrumentation (WMI) event class.

`vPropValue` Data type: `VARIANT`

Qualifiers: [in]

Pointer to the new value for the property.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded.

## Remarks

Your application must set the [EventType property](iccmevent--eventtype-property) before calling this method.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).