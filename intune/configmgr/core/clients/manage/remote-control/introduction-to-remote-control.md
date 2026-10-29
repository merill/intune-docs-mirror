---
layout: Conceptual
title: Remote control - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/introduction-to-remote-control
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
description: Get an introduction to remote control in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ff2a82c7-967e-8bac-e9d5-dcb7712ca996
document_version_independent_id: a16637c3-cebf-2b56-ecbf-b54397480d16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/remote-control/introduction-to-remote-control.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/remote-control/introduction-to-remote-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/remote-control/introduction-to-remote-control.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 3798dcec-23d2-d5ed-9b59-c6d41b11c88b
---

# Remote control - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use remote control to remotely administer, provide assistance, or view any client computer in the hierarchy. You can use remote control to troubleshoot hardware and software configuration problems on client computers and to provide support. Configuration Manager supports the remote control of all workgroup computers and domain-joined computers that run supported operating systems for the Configuration Manager client. For more information, see [Supported operating systems for clients and devices for Configuration Manager](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices)

Configuration Manager also lets you configure client settings to run Windows Remote Desktop and Remote Assistance from the Configuration Manager console.

Note

You cannot establish a Remote Assistance session from the Configuration Manager console to a client computer that is in a workgroup.

You can start a remote control session in the Configuration Manager console from **Assets and Compliance** &gt; **Devices**, from any device collection, from the Windows Command Prompt window, or from the Windows **Start** menu.