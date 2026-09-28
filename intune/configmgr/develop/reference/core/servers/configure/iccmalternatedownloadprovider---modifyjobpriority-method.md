---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider : ModifyJobPriority - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method
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
description: A method that tells the provider to modify the priority for a given job.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c512f104-29da-cd00-dc62-55e830fc5eaf
document_version_independent_id: c1536bfd-c6a0-d4d3-c18a-1432d70fb7b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 37f95a66-31fa-4415-423e-f3bea11ea074
---

# ICcmAlternateDownloadProvider : ModifyJobPriority - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::ModifyJobPriority** method, in Configuration Manager, instructs the provider to modify the priority for a given job.

## Syntax

```
HRESULT ModifyJobPriority(
        [in] REFGUID JobID,
        [in] CCM_DTS_PRIORITY Priority
        );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job on which to take action.

`Priority` Data type: `CCM_DTS_PRIORITY`

Qualifiers: [in]

The new priority.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Remarks

Note

An error should be returned if the job is not found or if modification of the priority failed. If any changes are required to make the guarantees described above on the comments on CCM\_DTS\_PRIORITY, the provider must make them. If the provider cannot honor that guarantee, it should report an error from this function.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).