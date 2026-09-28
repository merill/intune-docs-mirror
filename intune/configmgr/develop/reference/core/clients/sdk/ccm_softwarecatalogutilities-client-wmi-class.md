---
layout: Conceptual
title: CCM_SoftwareCatalogUtilities Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarecatalogutilities-client-wmi-class
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
description: The CCM_SoftwareCatalogUtilities WMI class is an SMS Provider server class, in Configuration Manager, that provides a set of utility methods to assist in processing software updates.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 08cc687d-98a1-c6a8-5513-9e1d7b079566
document_version_independent_id: d5ebef9b-3ff4-e6d2-3b2a-0f4e70561bb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarecatalogutilities-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_softwarecatalogutilities-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarecatalogutilities-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f82232e2-6d2f-4931-38e7-08058c6c996b
---

# CCM_SoftwareCatalogUtilities Class - Configuration Manager | Microsoft Learn

The `CCM_SoftwareCatalogUtilities` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a set of utility methods to assist in processing software updates.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_SoftwareCatalogUtilities :
{
};
```

## Methods

The following table lists the methods in the `CCM_SoftwareCatalogUtilities` class.

- [ApplyPolicyEx Method in Class CCM_SoftwareCatalogUtilities](applypolicyex-method-in-class-ccm_softwarecatalogutilities)
- [GetClientVersion Method in Class CCM_SoftwareCatalogUtilities](getclientversion-method-in-class-ccm_softwarecatalogutilities)
- [GetDeviceId Method in Class CCM_SoftwareCatalogUtilities](getdeviceid-method-in-class-ccm_softwarecatalogutilities)
- [GetPolicyState Method in Class CCM_SoftwareCatalogUtilities](getpolicystate-method-in-class-ccm_softwarecatalogutilities)
- [GetPortalUrlValue Method in Class CCM_SoftwareCatalogUtilities](getportalurlvalue-method-in-class-ccm_softwarecatalogutilities)
- [VerifySignature Method in Class CCM_SoftwareCatalogUtilities](verifysignature-method-in-class-ccm_softwarecatalogutilities)

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).