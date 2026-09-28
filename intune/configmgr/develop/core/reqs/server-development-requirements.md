---
layout: Conceptual
title: Server Development Requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements
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
description: The SMS Provider and associated technologies can be programmed by using managed code, VBScript, C++, and other languages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a9b45a14-76e7-0d04-b781-f1161e0dbbfd
document_version_independent_id: 5a7e8408-7e6e-b283-2d73-ce1095f9bb3c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/reqs/server-development-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/reqs/server-development-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/reqs/server-development-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 46122bec-8cb4-ae23-cc59-a0c1b73ff020
---

# Server Development Requirements - Configuration Manager | Microsoft Learn

In Configuration Manager, the SMS Provider and associated technologies can be programmed by using the following programming languages.

## Managed Code

The Configuration Manager SDK provides Microsoft .NET Framework libraries for accessing the SMS Provider and also for extending the Configuration Manager console.

Note

You can also use the System.Management namespace for accessing the SMS Provider, but this approach is not documented in the Configuration Manager SDK.

Programming the SMS Provider with managed code has the following requirements:

- Installed Configuration Manager site server
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly.
- Microsoft Visual Studio
- Microsoft .NET Framework version 4

### NET Framework

You should have version 4 of the .NET Framework installed on the development computer and on the computers you want to deploy your .NET Framework application to. To download the .NET Framework redistributable package, see [Download .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework). It is also installed as part of Visual Studio.

## Configuration Manager Console User Interface Extension

Programming Configuration Manager console extensions has the following requirements:

- Installed Configuration Manager site server
- Installed Configuration Manager console
- Microsoft Visual Studio
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly.
- Microsoft .NET Framework 4

    For more information, see [About console extensions](../servers/console/about-configuration-manager-console-extension).

    For specific information about deploying Configuration Manager console extensions, see [Configuration Manager Console Extension Deployment](../servers/console/console-extension-deployment)

## VBScript

You can use Windows Management Instrumentation (WMI) to access the SMS Provider.

The scripting samples are provided in VBScript and use WMI to access Configuration Manager. For more information, see [Objects overview](../understand/configuration-manager-objects-overview).

Programming the SMS Provider with VBScript has the following requirements:

- Installed Configuration Manager site server
- Windows Script Host

    For more information about scripting with WMI, see [Windows Management Instrumentation](/en-us/windows/win32/wmisdk/wmi-start-page).

## C++

C++ examples are provided for some Configuration Manager technologies where C++ is the most appropriate development language. In most cases, C++ developers should use the VBScript samples as a guide. For more information about using WMI with C++, see [Creating a WMI Application Using C++](/en-us/windows/win32/wmisdk/creating-a-wmi-application-using-c-).

## Other Languages

For languages that are not based on the .NET Framework, use the VBScript samples as a starting point for accessing Configuration Manager through WMI.

Important

For more information about general Configuration Manager requirements, see [Supported configurations](../../../core/plan-design/configs/supported-configurations).