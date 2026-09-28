---
layout: Conceptual
title: Status MIF Functions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/status-mif-functions
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
description: In Configuration Manager, status MIF functions are provided in separate libraries to create a status Management Information Format file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 409bc884-757f-89e6-0b92-c8c65ff33e79
document_version_independent_id: cf876f14-b83e-b0a9-27af-af5836a87d04
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/status-mif-functions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/status-mif-functions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/status-mif-functions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: c7b71c30-1206-4f90-9318-abb776cf1fc3
---

# Status MIF Functions - Configuration Manager | Microsoft Learn

In Configuration Manager, status MIF functions are provided in separate libraries to create a status Management Information Format (MIF) file. For more information about how the install status MIF file is used by Configuration Manager, see [SMS_Package Server WMI Class](../configure/sms_package-server-wmi-class).

Success or failure of an advertisement is determined by using either an install status MIF file or the exit code of the advertised program. Relying on the exit code limits the visibility of events during the installation process and requires interpretation of the various exit codes. However, using the install status MIF file provides an enhanced status indicating whether the installation succeeded or failed, and it includes an appropriate description.

## Status MIF Functions

- [Create Function](create-function)
- [InstallStatusMIF Function](installstatusmif-function)
- [InstallStatusMIFEx Function](installstatusmifex-function)