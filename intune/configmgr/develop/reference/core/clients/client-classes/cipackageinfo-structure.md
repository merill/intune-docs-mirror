---
layout: Conceptual
title: CIPackageInfo Structure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure
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
description: In Configuration Manager, the CIPackageInfo structure contains package information for a configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 664ada04-7061-d1f7-0bee-a3d191657832
document_version_independent_id: b39c1bd2-3076-54fb-be21-470f7be1374e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure.md
cmProducts: []
platformId: 823b6e36-f817-76e1-eec5-6636027f4933
---

# CIPackageInfo Structure - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CIPackageInfo` structure contains package information for a configuration item.

## Syntax

```
struct CIPackageInfo
{
      LPWSTR szTypeName;
      LPWSTR szPackageName;
      LPWSTR szPackageVersion;
      LPWSTR szNamespace;
};
```

## Members

szTypeName Name of the configuration item.

szPackageName Name of the package.

szPackageVersion Version of the package.

szNamespace Namespace used by the package software.