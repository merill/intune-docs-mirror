---
layout: Conceptual
title: RequestMachinePolicy Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client
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
description: In Configuration Manager, the RequestMachinePolicy method initiates a request for machine policy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 84c4b5b1-e733-88fe-bc52-391ea65203bd
document_version_independent_id: 73a7e944-e740-aae0-1011-7ca5c3e27753
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client.md
cmProducts: []
platformId: 90fc6595-1f18-acff-b27d-93184c201f63
---

# RequestMachinePolicy Method - Configuration Manager | Microsoft Learn

The `RequestMachinePolicy` method, in Configuration Manager, initiates a request for machine policy.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 RequestMachinePolicy(
      UInt32 uFlags
);
```

#### Parameters

`uFlags` Data type: `UInt32`

Qualifiers: [in]

Flags identifying the policy. Possible values are:

| Value | Description |
| --- | --- |
| 0 | A machine policy retrieval cycle is initiated. |
| 1 | A machine policy validation cycle is initiated, and the server and client cyclical redundancy checks (CRCs) are compared to verify that the policies are in agreement. If the policies aren't in agreement, then a resynchronization is initiated. |

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).