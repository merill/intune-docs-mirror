---
layout: Conceptual
title: Client Runtime Requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements
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
description: Learn about the client runtime requirements for applications that run on Microsoft Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2d186666-4d6d-9a3d-8e95-a1170af4a680
document_version_independent_id: 3a94f2ec-e85f-6b71-9a3a-09bacbd6238f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/client-runtime-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/client-runtime-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/client-runtime-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: f98dcf34-bece-fe54-cfb4-308b434b2b59
---

# Client Runtime Requirements - Configuration Manager | Microsoft Learn

Applications that run on Microsoft Configuration Manager clients have the following runtime requirements.

## Managed Code

- Configuration Manager client
- Microsoft .NET Framework version 4

## VBScript

- Configuration Manager client
- Windows Script Host

## Windows 64-Bit Support

A 32-bit compiled application that uses Configuration Manager SDK interfaces to access Configuration Manager client or Configuration Manager server functionality works when it runs in 32-bit emulation on a 64-bit Windows operating system. However, a 64-bit compiled application that uses Configuration Manager SDK interfaces that access 32-bit Configuration Manager client or Configuration Manager server functionality does not work. Similarly, Configuration Manager SDK scripts do not work when the scripting host is a native 64-bit application. A Configuration Manager SDK script does work if it is called from within a 32-bit scripting host.

The Configuration Manager client has a native 64-bit version that is installed automatically on Windows 64-bit operating systems. Applications that relied on the 32-bit interfaces to be present may need to be re-compiled in a native 64-bit environment to interact with the Configuration Manager client APIs.

## General Requirements

For more information about Configuration Manager client requirements, see [Supported configurations](../../../core/plan-design/configs/supported-configurations).