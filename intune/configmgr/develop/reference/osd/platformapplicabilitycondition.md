---
layout: Conceptual
title: PlatformApplicabilityCondition - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilitycondition
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
description: Learn how to specify one supported platform for an operating system deployment driver in Configuration Manager using PlatformApplicabilityCondition.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 29c375ff-235b-c505-704a-8bc2a6cd99d3
document_version_independent_id: 19fa6562-a1e7-1f6c-0383-71b7bf29dcaa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/platformapplicabilitycondition.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/platformapplicabilitycondition
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/platformapplicabilitycondition.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d5a200c4-2848-ebca-d202-e9a79a163410
---

# PlatformApplicabilityCondition - Configuration Manager | Microsoft Learn

`PlatformApplicabilityCondition` specifies one supported platform for an operating system deployment driver in Configuration Manager.

Note

It is only valid to populate this information with values from `SMS_SupportedPlatforms Server WMI Class` objects. Drivers can be targeted only at major releases, for example, all Windows.

**Type**: String.

**Instances**: Zero or more.

## Attributes

| Attribute | Description |
| --- | --- |
| DisplayName | The platform name displayed in the Configuration Manager console. |
| MaxVersion | The maximum supported version. For example, "5.20.9999.9999". |
| MinVersion | The minimum supported version. For example, "5.20.3790.0". |
| Name | The operating system name. For example, "Windows NT". |
| Platform | The supported platform, for example, "x64". |