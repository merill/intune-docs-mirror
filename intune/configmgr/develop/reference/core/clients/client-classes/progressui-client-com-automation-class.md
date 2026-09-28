---
layout: Conceptual
title: ProgressUI Client COM Automation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/progressui-client-com-automation-class
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
description: Learn how the ProgressUI is a COM automation class in Configuration Manager that represents a user interface that custom actions use to report progress to the Configuration Manager operating system deployment task sequencing environment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ed075b9e-96f9-7ae6-fa73-93ff89f643fe
document_version_independent_id: f50a2bf2-d632-dea7-2d3d-65f905a4b7e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/progressui-client-com-automation-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/progressui-client-com-automation-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/progressui-client-com-automation-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: e14a33f5-8ef9-b561-1879-7d5e2e8c9716
---

# ProgressUI Client COM Automation Class - Configuration Manager | Microsoft Learn

`ProgressUI` is a COM automation class in Configuration Manager that represents a user interface that custom actions use to report progress to the Configuration Manager operating system deployment task sequencing environment. The class implements the `IProgressUI` interface, which has a method `ShowActionProgress` that is used to display custom action progress information in a dialog box while the custom action is running. You shouldn't call any other method implemented in `ProgressUI`.