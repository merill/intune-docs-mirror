---
layout: Conceptual
title: How to use the conversion plug-in - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/how-to-use-plug-in
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
description: Use the Package Conversion Manager plug-in to customize the analysis and conversion processes.
ms.date: 2018-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: a94283b9-9289-dab6-e75a-2bba85274157
document_version_independent_id: 52a12675-ae6b-2fbe-62ba-fd4dccf6ad08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/how-to-use-plug-in.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/how-to-use-plug-in
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/how-to-use-plug-in.md
platformId: 5c3f9962-5789-50dd-ae84-1155be096eaa
---

# How to use the conversion plug-in - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Package Conversion Manager plug-in helps you customize the analysis and conversion processes. To use the Package Conversion Manager plug-in, write an executable or script file that performs custom operations. Then edit the configuration file, Microsoft.ConfigurationManagement.exe.config, to call the executable or script. The most common languages used to write the script are VBScript or PowerShell.

The Package Conversion Manager plug-in runs once for each package. If you analyze or convert multiple packages at one time, the Package Conversion Manager plug-in runs each time.

Note

For more information on the Package Conversion Manager elements in the Configuration Manager configuration file, see [Technical reference for the Package Conversion Manager plug-in configuration XML](plugin-config-xml).

## Default process

By default, Package Conversion Manager does the following actions:

1. Read a Configuration Manager package.
2. Create an application from the package, and add default attributes.
3. Analyze the application and determine a package readiness state.
4. Take one of the following actions, depending on the Package Conversion Manager operation:

    - **Analyze**: Display the package readiness state in the Configuration Manager console.
    - **Convert**: Write the application to the Configuration Manager database.

## Plug-in-based process

When you use the plug-in, Package Conversion Manager does the following actions:

1. Read a Configuration Manager package.
2. Create an application from the package, and add default attributes.
3. Convert the application to XML. Then save the file to disk.
4. Run the plug-in script to modify the application XML. For more information, see [Technical reference for the Package Conversion Manager plug-in configuration XML](plugin-config-xml).
5. Convert the application XML into a Configuration Manager application.
6. Analyze the application, and determine a package readiness state.
7. Take one of the following actions, depending on the Package Conversion Manager operation:

    - **Analyze**: Display the package readiness state in the Configuration Manager console.
    - **Convert**: Write the application to Configuration Manager database.