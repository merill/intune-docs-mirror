---
layout: Conceptual
title: How to Define the Hosting Technology - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-hosting-technology
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
description: The hosting technology is defined by implementing the `Microsoft.ConfigurationManagement.ApplicationManagement.HostingTechnology` class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: eecfb15f-b71c-6487-c0c9-d0542be8b10f
document_version_independent_id: 85fdabe2-4f89-48fa-b523-b673d45bebf2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-hosting-technology.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-hosting-technology
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-hosting-technology.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
platformId: bbdc45b8-fe63-412c-5989-83c2a8e54943
---

# How to Define the Hosting Technology - Configuration Manager | Microsoft Learn

To define a custom application management hosting technology, implement the `Microsoft.ConfigurationManagement.ApplicationManagement.HostingTechnology` class. The new class instance will define the hosting technology for a specific file type.

The HostingTechnology class supports run time interaction and configuration for technologies. The class contains the hosting rules as defined in the HostingTechnology.xml file. If needed, additional methods and properties can be added to this class, though in most cases the existing base should be sufficient.

In the Remote Desktop Protocol (RDP) sample project, a new hosting technology is required to handle Remote Desktop Protocol (RDP) files. Hosting support for RDP files is not built in to Configuration Manager, so a custom hosting technology is required.

Important

The HostingTechnology class name must match the class specified in the HostingTechnology.xml file.

### To define a custom hosting technology

1. Implement the `Microsoft.ConfigurationManagement.ApplicationManagement.HostingTechnology` class using the `Microsoft.ConfigurationManagement.ApplicationManagement.HostingTechnology` constructor.

    In the example, a string constant, defined in the Common class of the local project, is used for the string parameter. While the boolean parameter (`Microsoft.ConfigurationManagement.ApplicationManagement.HostingTechnology.IsRemote`) is set directly to true.

    The following example from the RDP sample project demonstrates how to define a hosting technology.

```
// Defines the hosting technology for RDP files. Hosting support for RDP files is not built in, so a custom
// hosting technology is needed on the client.
public class RdpHostingTechnology : HostingTechnology
{
    //   Initializes a new instance of the "RdpHostingTechnology" class.
    public RdpHostingTechnology()
       : base(Common.TechnologyId, true)
    {
    }
}
```

In the RDP sample project, a string constant for the TechnologyId is defined in the Common class of the local project.

```
//   Internal ID of the technology.
public const string TechnologyId = "Rdp";
```

#### Namespaces

Microsoft.ConfigurationManagement.ApplicationManagement

Microsoft.ConfigurationManagement.ApplicationManagement.Serialization

#### Assemblies

Microsoft.ConfigurationManagement.ApplicationManagement.dll

## .NET Framework Security