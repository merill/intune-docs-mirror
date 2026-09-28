---
layout: Conceptual
title: CCM_ProgramsManager Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class
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
description: In Configuration Manager, the CCM_ProgamsManager WMI class is a public client class that manages a specified software distribution program.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d5c2df42-c5b5-aadb-068b-111cf2a60450
document_version_independent_id: b2aa1260-102f-678c-332e-242b0a4d0ed3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6cf3e495-22f5-d8e3-1b06-d33dcaa4e4f7
---

# CCM_ProgramsManager Class - Configuration Manager | Microsoft Learn

The `CCM_ProgamsManager` WMI class is a public client class, in Configuration Manager, that manages a specified software distribution program.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_ProgramsManager();
```

## Methods

The following table shows the methods in the `CCM_ProgamsManager` class.

| Method | Description |
| --- | --- |
| [CancelDownload Method in Class CCM_ProgramsManager](canceldownload-method-in-class-ccm_programsmanager) | Cancels jobs that are downloading content that is required for legacy software distribution programs. |
| [ExecuteProgram Method in Class CCM_ProgramsManager](executeprogram-method-in-class-ccm_programsmanager) | Manages the download of a legacy software distribution program. |
| [ExecutePrograms Method in Class CCM_ProgramsManager](executeprograms-method-in-class-ccm_programsmanager) | Manages the download of a group of legacy software distribution programs. |
| [PostponeProgramsToNonBusinessHours Method in Class CCM_ProgramsManager](postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager) | Schedules legacy software distribution programs to run in the next available user-defined service window. |

## Properties

The `CCM_ProgamsManager` class does not define any properties.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).