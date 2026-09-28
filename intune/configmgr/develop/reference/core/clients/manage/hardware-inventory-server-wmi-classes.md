---
layout: Conceptual
title: Hardware inventory server WMI classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes
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
description: The Configuration Manager hardware inventory server WMI classes are generated dynamically and the name for a class is transformed from Win32_hardware to SMS_G_System_hardware.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7b44b8eb-35f1-9d97-1d69-1783fcf58a92
document_version_independent_id: c4761ec9-5fe5-f56e-06b4-d11c8b989dfa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: e1e2b25f-ff35-088a-0f75-8c728b16db0c
---

# Hardware inventory server WMI classes - Configuration Manager | Microsoft Learn

The Configuration Manager hardware inventory server WMI classes are generated dynamically.

During the Configuration Manager hardware inventory process, the name for a class is transformed from "Win32\_hardware" to "SMS\_G\_System\_hardware". For example, "Win32\_DiskDrive" translates to "SMS\_G\_System\_DISK".

In addition to the class name change, the following differences are found between the Win32 classes and the Configuration Manager hardware inventory server classes:

- Each Configuration Manager class inherits four properties from [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).
- The Configuration Manager hardware inventory classes don't support the Win32 class methods.
- Many of the Configuration Manager hardware inventory classes contain a subset of the Win32 class properties.