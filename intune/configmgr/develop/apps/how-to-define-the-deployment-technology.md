---
layout: Conceptual
title: How to Define the Deployment Technology - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-deployment-technology
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
description: To define a custom application management deployment technology, implement the Microsoft.ConfigurationManagement.ApplicationManagement.DeploymentTechnology class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 17101768-dbd0-9b75-2bf5-57d8cbb3c368
document_version_independent_id: 7e535ba2-7313-ac70-9bda-a5ea866053a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-deployment-technology.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-deployment-technology
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-deployment-technology.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
platformId: 86a76882-7ac5-e108-0071-01f3b20aaa05
---

# How to Define the Deployment Technology - Configuration Manager | Microsoft Learn

To define a custom application management deployment technology, implement the `Microsoft.ConfigurationManagement.ApplicationManagement.DeploymentTechnology` class. The new class instance will define the deployment technology used to deploy a specific application to devices.

The DeploymentTechnology class is the object that is registered with the Configuration Manager Application Model SDK. The DeploymentTechnology class contains references to three different types of objects that compose the technology. When implementing a new deployment technology you must implement a class that derives from this class.

In the Remote Desktop Protocol (RDP) sample project, a new deployment technology is required for Remote Desktop Protocol (RDP) files. Deployment support for RDP files is not built in to Configuration Manager, so a custom deployment technology is required.

Important

The DeploymentTechnology class name must match the class specified in the DeploymentTechnology.xml file.

### To define a custom deployment technology

1. Implement the `Microsoft.ConfigurationManagement.ApplicationManagement.DeploymentTechnology` class using the `Microsoft.ConfigurationManagement.ApplicationManagement.DeploymentTechnology` constructor. The string parameters are string values that uniquely identify the RDP Deployment Technology.

    Note

    The class constructor requires multiple instances of the string parameter that identifies the technology.

    The following example from the RDP sample project demonstrates how to define a deployment technology.

    ```
    namespace Microsoft.ConfigurationManagement.ApplicationManagement
    {
        //   Deployment technology used by RDP files.
        public class RdpDeploymentTechnology : DeploymentTechnology
        {
            // Initializes a new instance of the "RdpDeploymentTechnology" class.
             public RdpDeploymentTechnology()
                : base(Common.TechnologyId, Common.TechnologyId, Common.TechnologyId)
            {
            }
        }
    }
    ```

    In the RDP sample project, the string parameter is defined as a constant in the Common class of the local project.

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