---
layout: Conceptual
title: Server Runtime Requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements
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
description: Microsoft Configuration Manager server applications that are developed by using the Configuration Manager SDK, have the following runtime requirements.
ms.date: 2017-03-14T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: de99550e-629d-f151-0817-0c742d5ec167
document_version_independent_id: 322bb4ea-6053-cf53-0d96-cb7fb583c79a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/server-runtime-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/server-runtime-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/server-runtime-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 05104720-1038-7ad3-f2fe-3fd5ae0ef983
---

# Server Runtime Requirements - Configuration Manager | Microsoft Learn

Microsoft Configuration Manager server applications that are developed by using the Configuration Manager SDK, have the following runtime requirements.

## Managed Code

- A supported version of Windows Server as defined in [Supported operating systems for Configuration Manager site system servers](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers). For more information, see General Requirements.
- Installed Configuration Manager site server
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly
- Microsoft .NET Framework version 4

## Configuration Manager Console User Interface Extension

Programming Configuration Manager console extensions has the following requirements:

- Installed Configuration Manager site server
- Installed Configuration Manager console
- .NET Framework 4.0

    For more information, see [About console extensions](../servers/console/about-configuration-manager-console-extension).

## VBScript

- Installed Configuration Manager site server
- Windows Script Host

## Windows 64-Bit Support

A 32-bit compiled application that uses Configuration Manager SDK interfaces to access Configuration Manager client or Configuration Manager server functionality works when it runs in 32-bit emulation on a 64-bit Windows operating system. However, a 64-bit compiled application that uses Configuration Manager SDK interfaces that access 32-bit Configuration Manager client or Configuration Manager server functionality does not work. Similarly, Configuration Manager SDK scripts do not work when the scripting host is a native 64-bit application. A Configuration Manager SDK script does work if it is called from within a 32-bit scripting host.

## General Requirements

Important

For more information about general Configuration Manager requirements, see [Supported configurations for Configuration Manager](../../../core/plan-design/configs/supported-configurations).