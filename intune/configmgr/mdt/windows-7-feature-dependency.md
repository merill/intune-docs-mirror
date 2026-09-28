---
layout: Conceptual
title: Toolkit reference - Microsoft Deployment Toolkit (MDT) Windows 7 Feature Dependency Reference - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdt/windows-7-feature-dependency
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
description: Reference details for Microsoft Deployment Toolkit (MDT) Windows 7 Feature Dependency Reference
ms.date: 2016-09-09T00:00:00.0000000Z
ms.subservice: mdt
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1ff20211-ee77-f4d9-f2ef-c42d480b878b
document_version_independent_id: 1ff20211-ee77-f4d9-f2ef-c42d480b878b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdt/windows-7-feature-dependency.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdt/windows-7-feature-dependency
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdt/windows-7-feature-dependency.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 62230758-27b9-f7a4-ce80-9dd163140260
---

# Toolkit reference - Microsoft Deployment Toolkit (MDT) Windows 7 Feature Dependency Reference - Configuration Manager | Microsoft Learn

Table 8 lists the Windows 7 features, the parent feature, and any dependent features. You can use this information to determine which features and roles need to be installed to support a specific feature using the [Install Roles and Features](task-sequence-steps#install-roles-and-features) and [Uninstall Roles and Features](task-sequence-steps#uninstall-roles-and-features) task sequence steps.

## Table 8. Windows 7 Feature Dependency Reference

| **Feature** | **Parent Feature** | **Dependent Features** |
| --- | --- | --- |
| Windows Media® Center | Media Features | Might affect other Windows features |
| Windows DVD Maker | Media Features | Might affect other Windows features |
| Windows Media Player | Media Features | Might affect other Windows features |
| Windows Search | N/A | Might affect other Windows features |
| Internet Explorer (amd64) | N/A | Might affect other Windows features |
| World Wide Web services | Microsoft Internet Information Services (IIS) | - Microsoft Message Queuing (MSMQ) HTTP support - Windows Communication Foundation (WCF) HTTP activation |
| IIS 6 WMI compatibility | IIS, Web management tools, IIS 6 management compatibility | IIS 6 scripting tooling |
| Microsoft .NET extensibility | IIS, World Wide Web services, application development features | - Microsoft ASP.NET - MSMQ HTTP support - WCF HTTP activation |
| Default document | IIS, World Wide Web services, common HTTP features | MSMQ HTTP support |
| Directory browsing | IIS, World Wide Web services, common HTTP features | MSMQ HTTP support |
| HTTP redirection | IIS, World Wide Web services, common HTTP features | MSMQ HTTP support |
| Static content | IIS, World Wide Web services, common HTTP features | - Web-based Distributed Authoring and Versioning (WebDAV) publishing - MSMQ HTTP support |
| Custom logging | IIS, World Wide Web services, health and diagnostics | MSMQ HTTP support |
| HTTP logging | IIS, World Wide Web services, health and diagnostics | MSMQ HTTP support |
| ODBC logging | IIS, World Wide Web services, health and diagnostics | MSMQ HTTP support |
| Request Monitor | IIS, World Wide Web services, health and diagnostics | MSMQ HTTP support |
| Tracing | IIS, World Wide Web services, health and diagnostics | MSMQ HTTP support |
| Static content compression | IIS, World Wide Web services, performance features | MSMQ HTTP support |
| Security | IIS, World Wide Web services | - Microsoft .NET extensibility - MSMQ HTTP support - WCF HTTP activation |
| Request Filtering | IIS, World Wide Web services, security | - Microsoft .NET extensibility - MSMQ HTTP support - WCF HTTP activation |
| XPS Viewer | N/A | Might affect other Windows features |