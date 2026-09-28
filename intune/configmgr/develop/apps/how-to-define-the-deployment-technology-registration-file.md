---
layout: Conceptual
title: Define the Deployment Technology Registration File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-deployment-technology-registration-file
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
description: To define a deployment technology registration file, create an XML file based on the AppMgmtDigest schema.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 68b4bbb1-67ed-53c9-c28c-8003e6d94630
document_version_independent_id: cb968354-93ad-b97b-3e22-f11f3115bc95
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-deployment-technology-registration-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-deployment-technology-registration-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-deployment-technology-registration-file.md
cmProducts: []
platformId: 8d2bc882-89cf-2b79-1efd-4f5186b56ffc
---

# Define the Deployment Technology Registration File - Configuration Manager | Microsoft Learn

To define a deployment technology registration file, create an XML file based on the `http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest` schema. This registration file is Used in the installation process, and it registers the custom deployment technology with Configuration Manager. The deployment technology registration file is required for the installation of the custom deployment technology.

### To define the deployment technology registration file

1. Create a deployment technology registration file.

    The following example from the RDP sample project demonstrates how to define a deployment technology registration file.

    ```
    <AppMgmtDigest xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <DeploymentTechnology AuthoringScopeId="GLOBAL" LogicalName="RdpDeploymentTechnology" TechnologyId="Rdp" AssemblySuffix="Rdp" Version="1">
        <HostingTechnology>GLOBAL/RdpHostingTechnology</HostingTechnology>
        <InstallerTechnology>GLOBAL/RdpInstallerTechnology</InstallerTechnology>
      </DeploymentTechnology>
    </AppMgmtDigest>
    ```

| Attributes | Description |
| --- | --- |
| AuthoringScopeID | AuthoringScopeId will always be "GLOBAL". |
| LogicalName | LogicalName must match the name of the SDK class created in the SDK assembly. |
| TechnologyId | Technology must match the constant declared and used in the SDK assembly. |
| AssemblySuffix | AssemblySuffix must match the filename of the SDK assembly (Microsoft.ConfigurationManagement.ApplicationManagement.&lt;`AssemblySuffix`&gt;.dll). |
| Version | Version is the version number for the release of the deployment type extension. This version number is used for in-place revisions. |

| Element | Description |
| --- | --- |
| HostingTechnology | The HostingTechnology element must be "GLOBAL/&lt;`ClassNameForHostingTechnology`&gt;". |
| InstallerTechnology | The InstallerTechnology element must be "GLOBAL/&lt;`ClassNameForInstallerTechnology`&gt;". |