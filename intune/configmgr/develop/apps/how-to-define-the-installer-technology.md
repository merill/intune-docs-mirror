---
layout: Conceptual
title: How To Define the Installer Technology - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-installer-technology
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
description: Learn how to define the installer technology used to install a specific application to devices in Configuration Management.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9a50ba8b-e77b-c16d-53fc-4dd9a578fa6c
document_version_independent_id: 0d2c9e6d-017d-54a5-211e-51c5fb6f2395
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-installer-technology.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-installer-technology
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-installer-technology.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
platformId: fc458cf5-c4ef-195b-ce2d-96d6b1a570d7
---

# How To Define the Installer Technology - Configuration Manager | Microsoft Learn

To define the application management installer technology, implement the `Microsoft.ConfigurationManagement.ApplicationManagement.DeploymentTechnology.InstallerTechnology` class. The new class instance will define the installer technology used to install a specific application to devices.

The installer technology is a key extension point for extending the application model. This class is used to define specific metadata about the installation and detection of the technology on client systems concepts such as Detect, Install, and Uninstall.

In the Remote Desktop Protocol (RDP) sample project, a new installer technology is required for Remote Desktop Protocol (RDP) files. Deployment support for RDP files is not built-in to Configuration Manager, so a custom installer technology is required.

Important

The InstallerTechnology class name must match the class specified in the InstallerTechnology.xml file.

### To define a custom installer technology

1. Implement the `InstallerTechnology` class using the `Microsoft.ConfigurationManagement.ApplicationManagement.InstallerTechnology` constructor.

    The following example from the RDP sample project demonstrates how to define an installer technology.

    ```
    namespace RdpTechnology
    {
        //   Installer technology for RDP.
        public class RdpInstallerTechnology : InstallerTechnology
        {
            // Initializes a new instance of the "RdpInstallerTechnology" class.
             public RdpInstallerTechnology()
                : base(Common.TechnologyId, typeof(RdpInstaller), typeof(RdpContentImporter))
            {
            }
        }
    }
    ```

    In the RDP sample project, the string parameter is defined in the Common class. The RdpInstaller and RdpContentImporter classes are also defined in the RDP sample project.

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