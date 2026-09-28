---
layout: Conceptual
title: SDK what's new - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/changes/whats-new-sdk
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
description: Learn about the latest additions or changes to the Configuration Manager software development kit (SDK).
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 5892987f-c2c3-22c2-965c-39d843951447
document_version_independent_id: 7062c5a4-5c03-a226-e125-204ddca6b621
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/changes/whats-new-sdk.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/changes/whats-new-sdk
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/changes/whats-new-sdk.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 1a38c636-d957-94bb-5d0b-bfc3f369b9e6
---

# SDK what's new - Configuration Manager | Microsoft Learn

This article lists any recent additions or changes to the Configuration Manager software development kit (SDK).

## External dependencies require .NET 4.6.2

Starting in version 2111, all Configuration Manager libraries are built using Microsoft .NET Framework version 4.6.2 or later. If you develop an application or tool that depends upon these libraries, it also needs to support .NET 4.6.2 or later. Microsoft recommends using .NET Framework version 4.8.

Applications or tools that use Configuration Manager WMI classes and methods, REST APIs, or PowerShell cmdlets aren't affected.

If you develop a third-party add-on to Configuration Manager, you should test your add-on with every monthly [technical preview branch release](../../../core/get-started/technical-preview). Regular testing helps confirm compatibility, and allows for early reporting of any issues with standard interfaces.

## Configuration Manager SDK redistributable files available on NuGet

### Client messaging

[Client messaging SDK package](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.Messaging/)

### Management point API (MPAPI)

The MPAPI contains the management point interface libraries.

- [Microsoft.ConfigurationManagement.MPAPI.i386](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.MPAPI.i386/)
- [Microsoft.ConfigurationManagement.MPAPI.amd64](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.MPAPI.amd64/)

For more information, see the [MPAPI documentation](/en-us/previous-versions/system-center/developer/cc144951%28v=msdn.10%29).

### Install status MIF COM library (ISMIFCOM)

ISMIFCOM is a COM library with a class wrapper for the install status MIF functions.

- [Microsoft.ConfigurationManagement.ISMIFCOM.i386](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.ISMIFCOM.i386/)
- [Microsoft.ConfigurationManagement.ISMIFCOM.amd64](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.ISMIFCOM.amd64/)

For more information, see the [ISMIFCOM documentation](../../reference/core/servers/manage/status-mif-functions).

### Data discovery record creation libraries

SMSRsGen and SMSRsGenCtl are legacy COM libraries used to create data discovery records (DDRs).

Important

These are legacy libraries. The current recommendation is to use the Client Messaging SDK [DiscoveryDataRecordFile class](/en-us/previous-versions/system-center/developer/mt778052%28v=cmsdk.12%29). Use the latest [Client Messaging SDK package](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.Messaging/) from NuGet.

- [Microsoft.ConfigurationManagement.SMSRsGen.i386](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGen.i386/)
- [Microsoft.ConfigurationManagement.SMSRsGen.amd64](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGen.amd64/)
- [Microsoft.ConfigurationManagement.SMSRsGenCtl.i386](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGenCtl.i386/)
- [Microsoft.ConfigurationManagement.SMSRsGenCtl.amd64](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGenCtl.amd64/)

For more information, see the [SMSResGen documentation](../../reference/core/servers/configure/smsresgen-com-automation-class)