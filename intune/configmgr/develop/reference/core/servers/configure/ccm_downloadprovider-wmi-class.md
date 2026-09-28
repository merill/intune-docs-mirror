---
layout: Conceptual
title: CCM_DownloadProvider Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_downloadprovider-wmi-class
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
description: In Configuration Manager, the CCM_DownloadProvider class defines and registers an Alternate Content Provider (ACP).
ms.date: 2026-04-14T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e7de582c-4ce8-7e64-c27d-c5c3fc3acba7
document_version_independent_id: e7de582c-4ce8-7e64-c27d-c5c3fc3acba7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ccm_downloadprovider-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ccm_downloadprovider-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ccm_downloadprovider-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: 08dbc2b6-fac8-133e-8dac-babe52b2bd7f
---

# CCM_DownloadProvider Class - Configuration Manager | Microsoft Learn

The **CCM\_DownloadProvider** class, in Configuration Manager, defines and registers an Alternate Content Provider (ACP). It's a non-Microsoft download plug-in that the Configuration Manager client can use to download content. The provider must be registered on the client by using this class before it can be used.

## Syntax

```
class CCM_DownloadProvider: CCM_Policy
{
    string  LogicalName;
    string  CLSID;
    uint32  Priority;
    String  GlobalSettings;
    string  Reserved;
};

```

#### Parameters

`LogicalName` Data type: String

Qualifiers: [in, RealKey, NotNull: ToInstance ToSubClass]

The name of the non-Microsoft provider. This field must match the value specified to the SMS provider.

`CLSID` Data type: String

Qualifiers: [in, NotNull: ToInstance, ToSubClass]

The COM class ID corresponding to the interface implementation.

`Priority` Data type: String

Qualifiers: [in, NotNull: ToInstance ToSubClass]

Priority in the face of multiple alternate provider choices. For future use. Must be nonzero.

`GlobalSettings` Data type: String

Qualifiers: [in]

Provider specific data. Use this property for any client-wide configuration for the provider.

`PolicySource` Data type: String

Qualifiers: [in]

The source of the policy, typically "Local" when the instance is created on a client in the root\ccm\policy\machine\RequestedConfig namespace. Not available in root\ccm\policy\machine\ActualConfig namespace that contains compiled policy.

`Reserved` Data type: String

Qualifiers: [in]

Reserved for future use.

## Return Values

None.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).