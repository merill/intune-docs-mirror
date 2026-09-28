---
layout: Conceptual
title: Client Development Requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements
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
description: The Configuration Manager client can be programmed by using programming languages that follow.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 88ea22f0-56b9-0b4f-adbb-9705ae791452
document_version_independent_id: 44058b6b-9433-b39b-ea9a-a756624bac69
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/client-development-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/client-development-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/client-development-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 7a8a826e-d87b-85f6-f240-305eccc92a14
---

# Client Development Requirements - Configuration Manager | Microsoft Learn

The Configuration Manager client can be programmed by using the following programming languages.

## Managed Code

If you are programming the Configuration Manager client by using managed code, you use the System.Management namespace and, where applicable, you use COM Interoperability to access the Configuration Manager automation objects.

### NET Framework

You should have version 4.0 of the Microsoft .NET Framework installed on the development computer and on the computers you want to deploy your .NET Framework application to. To download the .NET Framework redistributable package, see [Download .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework). It is also installed as part of Visual Studio.

## VBScript

You can use VBScript to access the Configuration Manager client WMI namespaces. The client also has a number of COM automation objects that you can use.

For more information about scripting with WMI, see [Windows Management Instrumentation](/en-us/windows/win32/wmisdk/wmi-start-page).

## C++

C++ examples are provided for some Configuration Manager technologies where C++ is the most appropriate development language. In most cases, C++ developers should use the VBScript samples as a guide. For more information about using WMI with C++, see [Creating a WMI Application Using C++](/en-us/windows/win32/wmisdk/creating-a-wmi-application-using-c-).

## Other Languages

For languages that are not based on .NET Framework, use the VBScript samples as a starting point for accessing Configuration Manager through WMI.

Important

For more information about general Configuration Manager requirements, see [Supported configurations](../../../core/plan-design/configs/supported-configurations).