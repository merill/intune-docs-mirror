---
layout: Conceptual
title: The content library - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/the-content-library
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
description: Learn about the content library that Configuration Manager uses to reduce the overall size of distributed content.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 36d316a0-555f-f1bc-8f73-7720f5fab509
document_version_independent_id: dba87ce9-542b-efa2-234c-bfcebfa38089
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/the-content-library.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/the-content-library
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/the-content-library.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 7dcbe470-52e4-77b3-a41c-9d43afa399e5
---

# The content library - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The content library is a single-instance store of content in Configuration Manager. The site uses it to reduce the overall size of the combined body of content that you distribute. The content library stores all content files for software deployments, for example: software updates, applications, and OS deployments.

- The site automatically creates and maintains a copy of the content library on each site server and each distribution point.
- Before Configuration Manager adds content files to the site server or copies the files to distribution points, it verifies whether each content file is already in the content library.
- If the content file is available, Configuration Manager doesn't copy the file. It instead associates the existing content file with the application or package.

On distribution point servers, configure the following options:

- One or more disk drives on which you want to create the content library.
- A priority for each drive that you use.

Configuration Manager copies content files to the drive with the highest priority until that drive contains less than a minimum amount of free space that you specify.

- You configure the drive settings during the distribution point installation.
- You can't configure the drive settings in the distribution point properties after the installation has finished.

For more information about how to configure the drive settings for the distribution point, see [Manage content and content infrastructure](../../servers/deploy/configure/manage-content-and-content-infrastructure).

Note

To move the content library to a different location on a distribution point after the installation, use the **Content Library Transfer** tool in the Configuration Manager tools. For more information, see the [Content Library Transfer tool](../../support/content-library-transfer).

## About the content library on the CAS

By default, Configuration Manager creates a content library on the central administration site (CAS) when the site is installed. The content library is placed on the drive of the site server that has the most free disk space. Because you can't install a distribution point on the CAS, you can't prioritize the drives for use by the content library. Similar to the content library on other site servers and on distribution points, when the drive that contains the content library runs out of available disk space, the content library automatically spans to the next available drive.

Configuration Manager uses the content library on the CAS in the following scenarios:

- You create content on the CAS.
- You migrate content from another Configuration Manager site, and assign the CAS as the site that manages that content.

Note

When you create content at a primary site, and then distribute it to a different primary site or a secondary site below a different primary site, the CAS temporarily stores that content in its scheduler inbox. It doesn't add that content to its content library.

Use the following options to manage the content library on the CAS:

- To prevent the content library from being installed on a specific drive, create an empty file named **NO\_SMS\_ON\_DRIVE.SMS**. Copy it to the root of the drive before the content library is created.
- After the content library has been created, use the **Content Library Transfer** tool from the Configuration Manager tools to manage the location of the content library. For more information, see the [Content Library Transfer tool](../../support/content-library-transfer).

Note

Content-enabled cloud management gateways don't use single-instance storage. The site encrypts packages before sending to Azure, and each package has a unique encrypted key. Even if two files were identical, the encrypted versions wouldn't be the same.

## Inside the content library

Warning

The following section is provided for informational purposes only. Don't alter, add, or remove any files or folders in the content library. Doing so could corrupt packages, contents, or the content library as a whole. If you suspect any missing, corrupt, or otherwise invalid data, use the validation feature in the Configuration Manager console to detect such issues. Then redistribute the affected content to correct the issues.

By default, the content library is stored on the root of a drive in a folder called **SCCMContentLib**. This folder is shared by default as **SCCMContentLib$**. The folder and share have restricted permissions to prevent accidental damage. All changes should be made from the Configuration Manager console. Within this folder are the following objects:

- The package library (**PkgLib** folder): Information about what packages are present on the distribution point.
- The data library (**DataLib** folder): Information about the original structure of the packages.
- The file library (**FileLib** folder): The original files in the package. This folder is typically what uses the bulk of the storage.

[![Diagram overview of Configuration Manager content library.](media/content-library-overview.png)](media/content-library-overview.png#lightbox)

Tip

Use the **Content Library Explorer** tool from the Configuration Manager tools to browse the contents of the content library. You can't use this tool to modify the contents. It provides insight into what's present, as well as allowing validation and redistribution. For more information, see the [Content Library Explorer](../../support/content-library-explorer).

### Package library

The package library folder, **PkgLib**, includes one file for each package distributed to the distribution point. The file name is the package ID, for example, `ABC00001.INI`. In this file under the `[Packages]` section is a list of content IDs that are part of the package, as well as other information such as the version. For example, **ABC00001** is a legacy package at version **1**. The content ID in this file is `ABC00001.1`.

### Data library

The data library folder, **DataLib**, includes one file and one folder for each of the contents in each package. For example, this file and folder are named `ABC00001.1.INI` and `ABC00001.1`, respectively. The file includes information for validation. The folder recreates the folder structure from the original package.

The files in the data library are replaced by INI files with the name of the original file in the package. For example, `MyFile.exe.INI`. These files include information about the original file, such as the size, time modified, and the hash. Use the first four characters of the hash to locate the original file in the file library. For example, the hash in MyFile.exe.INI is **DEF98765**, and the first four characters are **DEF9**.

### File library

If the content library spans across multiple drives, the package files could be in the file library folder, **FileLib**, on any of these drives.

Locate a specific file using the first four characters from the hash found in the data library. Inside the file library folder are many folders, each with a four-character name. Find the folder that matches the first four characters from the hash. Once you find this folder, it includes one or more sets of three files. These files share the same name, but one has the extension INI, one has the extension SIG, and one has no file extension. The original file is the one with no extension whose name is equal to the hash from the data library.

For example, folder **DEF9** includes `DEF98765.INI`, `DEF98765.SIG`, and `DEF98765`. `DEF98765` is the original `MyFile.exe`. The INI file includes a list of "users" or content IDs that share the same file. The site doesn't remove a file unless all of these contents are also removed.

### Drive spanning

The content library can be spanned across multiple drives. You choose these drives when creating the distribution point. By default, Configuration Manager automatically chooses the drives when spanning the content library.

When you choose the drives, select a primary and secondary drive. The site stores all metadata on the primary drive. It only spans the file library across to the secondary drive. The folder's share name for secondary drives includes the drive letter. For example, if D: and E: are secondary drives for the content library, the share names are **SCCMContentLibD$** and **SCCMContentLibE$**.

If you chose the **Automatic** option, Configuration Manager selects the drive with the most available free space as its primary drive. It stores all of the metadata on this drive. The site only spans the file library across to secondary drives.

You specify a reserve space amount during configuration. Configuration Manager attempts to use a secondary disk once the best available disk has only this reserve space amount left free. Each time a new drive is selected for use, the drive with the most available free space is selected.

You can't specify that a distribution point should use all drives except for a specific set. Prevent this behavior by creating an empty file on the root of the drive, called `NO_SMS_ON_DRIVE.SMS`. Place this file before Configuration Manager selects the drive for use. If Configuration Manager detects this file on the root of the drive, it doesn't use the drive for the content library.

## Troubleshoot

The following tips may help you troubleshoot issues with the content library:

- Review the logs on the site server (**distmgr.log** and **PkgXferMgr.log**) and the distribution point (**smsdpprov.log**) for any pointers to the failures.
- Use the [Content Library Explorer](../../support/content-library-explorer) tool.
- Check for file locks by other processes, such as antivirus software. Exclude the content library on all drives from automatic antivirus scans, as well as the temporary staging directory, **SMS\_DP$**, on each drive.
- To see if there are any hash mismatches, validate the package from the Configuration Manager console.
- As a last option, redistribute the content. This action should resolve most issues.

For more in-depth information, see [Understand and troubleshoot content distribution](/en-us/troubleshoot/mem/configmgr/content-distribution-introduction).