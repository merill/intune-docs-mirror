---
layout: Conceptual
title: ResetPolicy Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client
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
description: Learn how to reset the policy on a client resulting in the next policy request receiving a full policy in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 665b1ea9-8eb7-6669-cb0c-83f8b73c5d5b
document_version_independent_id: 0a8216ae-ff08-8cf7-aadb-918b0e1e19e3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client.md
cmProducts: []
platformId: 929af6a6-e843-6743-e996-1a25ccfc15bb
---

# ResetPolicy Method - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ResetPolicy` method, resets the policy on a client. As a result, the next policy request will receive a full policy instead of merely the change in policy since the last policy request.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 ResetPolicy(
     UInt32 uFlags
);
```

#### Parameters

`uFlags` Data type: `UInt32`

Qualifiers: [in]

Flags identifying the policy. Possible values are:

| Value | Description |
| --- | --- |
| 0 | The next policy request will be for a full policy instead of the change in policy since the last policy request. |
| 1 | The existing policy will be purged completely. |

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Remarks

Indiscriminate calling of this method could have adverse effects. For example, if you purge the existing policy (`ulFlags` = 1) software distribution programs could be run more than once. If the request is for full policy (`ulFlags` = 0), you could generate unnecessary network traffic.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).