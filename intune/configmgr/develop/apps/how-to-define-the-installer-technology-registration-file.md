---
layout: Conceptual
title: Define the Installer Technology Registration File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-installer-technology-registration-file
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
description: Learn how to register the custom installer technology with Configuration Manager using an XML file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 62a70806-6422-7b01-5647-b4c0bdca3b88
document_version_independent_id: 5d964e29-8af2-e873-2a97-b14c8abde6b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-installer-technology-registration-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-installer-technology-registration-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-installer-technology-registration-file.md
cmProducts: []
platformId: ddeccc0d-8a18-15a5-a6aa-756739140017
---

# Define the Installer Technology Registration File - Configuration Manager | Microsoft Learn

To define an installer technology registration file, create an XML file based on the `http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest` schema. Used in the installation process, the registration file registers the custom installer technology with Configuration Manager. The deployment technology registration file is required for the installation of the custom installer technology.

### To define the installer technology registration file

1. Create an installer technology registration file.

    The following example from the RPC sample project demonstrates how to define an installer technology registration file.

    ```
    <AppMgmtDigest xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <InstallerTechnology AuthoringScopeId="GLOBAL" LogicalName="RdpInstallerTechnology" InstallerId="Rdp" AssemblySuffix="Rdp" Version="1" />
    </AppMgmtDigest>
    ```

| Attributes | Description |
| --- | --- |
| AuthoringScopeID | AuthoringScopeId will always be "GLOBAL". |
| LogicalName | LogicalName must match the name of the SDK class created in the SDK assembly for InstallerTechnology. |
| HostingId | HostingId must match the constant declared and used in the SDK assembly for InstallerTechnolgy. |
| AssemblySuffix | AssemblySuffix must match the filename of the SDK assembly (Microsoft.ConfigurationManagement.ApplicationManagement.&lt;`AssemblySuffix`&gt;.dll). |
| Version | Version is the version number for the release of the deployment type extension. This version number is used for in-place revisions. |