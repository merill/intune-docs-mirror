---
layout: Conceptual
title: ICCMEvent::SubmitPending Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method
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
description: Learn how to submit an event that is stored by Windows Management Instrumentation (WMI) using the ICcmEvent::SubmitPending method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 230204fe-c993-479f-40dd-e57aec50e6ab
document_version_independent_id: fe0db800-cfe7-2bd7-a14e-21c07a80ee75
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5dce893b-b3c7-5081-37e0-9e5d121f5272
---

# ICCMEvent::SubmitPending Method - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ICcmEvent::SubmitPending` method submits an event that is stored by Windows Management Instrumentation (WMI).

## Syntax

```
[C++]
HRESULT ICcmEvent::SubmitPending(
      BSTR bstrEventID,
      long lFlags
);
```

#### Parameters

`bstrEventID` Data type: `BSTR`

Qualifiers: [in, optional, defaultvalue("0")]

Reserved. Must be `null`.

`lFlags` Data type: `long`

Qualifiers: [in, optional, defaultvalue(0)]

Reserved. Must be zero.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

Your application should use this method instead of the [Submit method](iccmevent--submit-method) in situations where the Configuration Manager Agent Host (CCMEXEC) service might not be running. Instead of directly calling CCMEXEC to submit the event, this method stores it in WMI. If the service is running, the event is picked up immediately and issued. Otherwise, it's issued the next time the service starts.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).