---
layout: Conceptual
title: About Configuration Manager SDK Requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements
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
description: Learn how developing applications and scripts for Microsoft Configuration Manager can be done using a number of development languages and tools.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: c9e690f5-ee42-9daf-4eb5-83354a2a238e
document_version_independent_id: 8b033647-28b3-35c2-30b0-13fd4f927ba6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
platformId: e7c06265-d745-11cd-4d53-629a47125632
---

# About Configuration Manager SDK Requirements - Configuration Manager | Microsoft Learn

Developing applications and scripts for Microsoft Configuration Manager can be done using a number of development languages and tools. Which one you use depends on the type of application you are writing. Large applications will likely be written in C# using the managed Configuration Manager SDK libraries. VBScript is a good choice for scripting Configuration Manager.

This documentation provides examples in C#, VBScript and, where appropriate, C++.

Note

If you are programming with another .NET Framework language, use the C# examples for reference.

## Development tools

Visual Studio provides a suitable environment for developing Configuration Manager applications and scripts. For more information, see [Visual Studio documentation](/en-us/visualstudio).

## Development Requirements

For information about development requirements, see [Configuration Manager Client Development Requirements](client-development-requirements) and [Configuration Manager Server Development Requirements](server-development-requirements).

## Runtime Requirements

For information about runtime requirements, see [Configuration Manager Client Runtime Requirements](client-runtime-requirements) and [Configuration Manager Server Runtime Requirements](server-runtime-requirements).

Important

For more information about general Configuration Manager requirements, see [Supported configurations](../../../core/plan-design/configs/supported-configurations).