---
layout: Conceptual
title: SDK libraries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files
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
description: Use Configuration Manager libraries when you write unmanaged applications.
ms.date: 2021-11-18T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 3a147d45-1e29-7fb2-031e-31d05b76b83f
document_version_independent_id: 5a202ff3-0c8b-877f-7968-321cd196f1c4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 985ad24a-3111-b3e3-b88d-b3115f9021eb
---

# SDK libraries - Configuration Manager | Microsoft Learn

In Configuration Manager, when you write unmanaged applications, you might have to include one or more of the following libraries. Use COM Interoperability to access COM objects from .NET Framework applications.

| Library | Description |
| --- | --- |
| ismifcom.dll | Contains a class wrapper for the install status MIF functions. Visual Basic and scripting programmers use this ActiveX control to create a status MIF file. Visual Basic users must select the ISMIFCOM 1.0 Type Library project reference. Scripting users create this object by using "ISMIFCOM.InstallStatusMIF". |
| Microsoft.ConfigurationManager.Messaging.dll | Contains A .NET assembly encapsulating the client SDK that has an object model and transport for communicating with Configuration Manager site server roles such as the management point. |
| smsmsgapi.dll | Contains management point interface libraries. |
| smsrsgen.dll | Contains the Discovery Data Record functions. This DLL must exist in the directory from where you start your application. |
| smsrsgenctl.dll | Contains a class wrapper for the Discovery Data Record Functions. Visual Basic and scripting programmers use this control to create discovery data records. |

Note

The library files are available as [NuGet packages](https://www.nuget.org/profiles/ConfigurationManagerTeam).

For more information about general Configuration Manager requirements, see [Supported configurations](../../../core/plan-design/configs/supported-configurations).