---
layout: Conceptual
title: About Creating a Data Discovery Record - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-creating-a-data-discovery-record
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
description: Learn how to create data discovery records (DDRs), using the SMSRsGenCtl.dll and other functions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: b8a21190-c29d-ea46-ccef-8a24dda43b2e
document_version_independent_id: 345ca2e0-0cf6-d7b5-ce49-1f2229311544
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/about-creating-a-data-discovery-record.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/about-creating-a-data-discovery-record
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/about-creating-a-data-discovery-record.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 7cec6c31-0239-f74d-48e7-861d5e4a33b2
---

# About Creating a Data Discovery Record - Configuration Manager | Microsoft Learn

To create data discovery records (DDRs), you must use the SMSRsGenCtl.dll and the functions that are described in the following table. These functions create a single DDR that can be process by Data Discovery Manager (DDM). The order in which you call the functions is important; you must call `DDRNew` before calling any of the functions that add properties. The order in which you add properties to your class is arbitrary. However, the last function you call must be `DDRWrite` to create the DDR. The DDR must then be manually copied to the SMS\Inboxes\Auth\Ddm.box directory.

DDRs that fail to process are moved to the SMS\Inboxes\Ddm.box\Bad\_ddrs directory. If you have logging turned on, you can view the DDM.log file for an explanation of the failure. After fixing the source of the errors, you can rerun your program to load the DDR.

C programmers can use the SMSRsGen.dll file to access the DDR functions. Visual Basic programmers can use the SMSRsGenCtl.dll to access the DDR methods. These methods have the same name and parameters as the C library functions.

Because the `SMSResGen` control is not thread safe, do not try to create more than one instance of the class.

The `SMSResGen` method has the following functions:

Important

The function `DDRSendToSMS`, available in previous releases of the SDK and in versions of `SMSRsGen.dll` and `SMSRsGenCtl.dll`, has been deprecated and should not be used with Configuration Manager.

[DDRNew](../../../reference/core/servers/configure/ddrnew) Creates a new DDR.

[DDRAddInteger](../../../reference/core/servers/configure/ddraddinteger) Adds an integer property to the DDR.

[DDRAddString](../../../reference/core/servers/configure/ddraddstring) Adds a string property to the DDR.

[DDRAddIntegerArray](../../../reference/core/servers/configure/ddraddintegerarray) Adds an integer array property to the DDR.

[DDRAddStringArray](../../../reference/core/servers/configure/ddraddstringarray) Adds a string array property to the DDR.

[DDRWrite](../../../reference/core/servers/configure/ddrwrite) Writes the DDR to a file.