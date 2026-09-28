---
layout: Conceptual
title: CCM_CTM_JobStateEx4 Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_ctm_jobstateex4-class
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
description: Learn how to represent the state information for a single Content Transfer Manager job using CCM_CTM_JobStateEx4 class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 46be119e-c48d-4c1b-9357-bde54b91f866
document_version_independent_id: 917c16ff-78ba-95e0-21c7-fb921af78fd4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ccm_ctm_jobstateex4-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ccm_ctm_jobstateex4-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ccm_ctm_jobstateex4-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: 6f296d1c-0c98-7e85-ec14-89b91b819931
---

# CCM_CTM_JobStateEx4 Class - Configuration Manager | Microsoft Learn

The **CCM\_CTM\_JobStateEx4** class, in Configuration Manager, represents the state information for a single Content Transfer Manager job.

## Syntax

```
class CCM_CTM_JobStateEx4
{
    string ProviderSettingsFromRequest;
    uint32 CurrentProviderPriority;
    string CurrentProviderLogicalName;
    string CurrentProviderCLSID;
    string CurrentProviderGlobalSettings;
    string CurrentProviderSettingsFromRequest;
};

```

#### Parameters

`ProviderSettingsFromRequest` Data type: String

Qualifiers: [in]

XML describing the allowed alternate providers and provider-specific settings.

`CurrentProviderPriority` Data type: UInt32

Qualifiers: [in]

Priority in the face of multiple alternate provider choices. For future use.

`CurrentProviderLogicalName` Data type: String

Qualifiers: [in]

The name of the current provider. This value must match the value specified to the SMS provider.

`CurrentProviderCLSID` Data type: String

Qualifiers: [in]

The COM class ID corresponding to the current provider.

`CurrentProviderGlobalSettings` Data type: String

Qualifiers: [in]

Provider-specific data for the current provider.

`CurrentProviderSettingsFromRequest` Data type: String

Qualifiers: [in]

Provider-specific settings for the current provider.

## Return Values

None.

## Remarks

There will be an instance of this class for each job started by the Content Transfer Manager.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).