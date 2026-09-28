---
layout: Conceptual
title: Console ResourceAssembly Element - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-resourceassembly-element
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
description: Learn how to define the resources that are used by the node with the ResourceAssembly element in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 23dce61a-b605-406b-87bc-445a21cee630
document_version_independent_id: 2af83241-b360-99f1-ecdb-656f94419641
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-resourceassembly-element.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-resourceassembly-element
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-resourceassembly-element.md
cmProducts: []
platformId: 2c1537d9-e563-f02c-66d6-b349200c37fc
---

# Console ResourceAssembly Element - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ResourceAssembly` element defines the resources that are used by the node. The following XML defines the assembly, `AdminUI.CollectionProperty.dll`, and the type of the resource within the assembly.

```
<ResourceAssembly>
    <Assembly>AdminUI.CollectionProperty.dll</Assembly>
    <Type>Microsoft.ConfigurationManagement.AdminConsole.CollectionProperty.Properties.Resources.resources</Type>
</ResourceAssembly>

```