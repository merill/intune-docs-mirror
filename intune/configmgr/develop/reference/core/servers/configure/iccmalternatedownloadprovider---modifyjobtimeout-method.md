---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider : ModifyJobTimeout - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobtimeout-method
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
description: Learn how to use ICcmAlternateDownloadProvider::ModifyJobTimeout method to instruct the provider to modify the timeout for a given job.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9296acdb-89b8-56dc-70aa-d1ba2c767d6d
document_version_independent_id: 0658c3e2-ea15-23a1-160e-1c4ebeef28e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobtimeout-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobtimeout-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobtimeout-method.md
cmProducts: []
platformId: 250dd865-0206-a92f-6d15-f788832e5f85
---

# ICcmAlternateDownloadProvider : ModifyJobTimeout - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::ModifyJobTimeout** method, in Configuration Manager, instructs the provider to modify the timeout for a given job.

## Syntax

```
HRESULT ModifyJobTimeout(
            REFGUID JobID,
            DWORD dwTimeoutSeconds
    );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job on which to take action.

`dwTimeoutSeconds` Data type: `DWORD`

Qualifiers: [in]

The new timeout.

## Remarks

Note

An error should be returned if the job is not found or if modification of the timeout failed. If the new timeout results in the job immediately timing out, the call should complete and then the provider should notify Content Transfer Manager of the error using SendNotifyErrorToCTM.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).