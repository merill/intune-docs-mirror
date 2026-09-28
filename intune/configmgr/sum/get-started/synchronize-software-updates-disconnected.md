---
layout: Conceptual
title: Synchronize updates with no Internet connection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/synchronize-software-updates-disconnected
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
description: Run software updates synchronization on the top-level software update point that is disconnected from the Internet.
ms.date: 2020-02-13T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: 66e1d405-27b7-c956-f64c-b289ff1c08f7
document_version_independent_id: f46aa37b-9c6a-f2ef-8436-beac6e867ad6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/get-started/synchronize-software-updates-disconnected.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/get-started/synchronize-software-updates-disconnected
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/get-started/synchronize-software-updates-disconnected.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: c36a9ace-de16-33c2-f403-c4ca4cb0271c
---

# Synchronize updates with no Internet connection - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When the software update point at the top-level site is disconnected from the Internet, you must use the export and import functions of the WSUSUtil tool to synchronize software updates metadata. You can choose an existing WSUS server not in your Configuration Manager hierarchy as the synchronization source. This article provides information about how to use the export and import functions of the WSUSUtil tool.

To export and import software updates metadata, you must export software updates metadata from the WSUS database on a specified export server, then copy the locally stored license terms files to the disconnected software update point, and then import the software updates metadata to the WSUS database on the disconnected software update point.

Use the following table to identify the export server in which to export the software updates metadata.

| Software update point | Upstream update source for connected software update points | Export server for a disconnected software update point |
| --- | --- | --- |
| Central administration site | Microsoft Update (Internet) Existing WSUS server | Choose a WSUS server that is synchronized with Microsoft Update by using the software update classifications, products, and languages that you need in your Configuration Manager environment. |
| Stand-alone primary site | Microsoft Update (Internet) Existing WSUS server | Choose a WSUS server that is synchronized with Microsoft Update by using the software update classifications, products, and languages that you need in your Configuration Manager environment. |

Before you start the export process, verify that software updates synchronization is completed on the selected export server to ensure that the most recent software updates metadata is synchronized. To verify that software updates synchronization has completed successfully, use the following procedure.

#### To verify that software updates synchronization has completed successfully on the export server

1. Open the WSUS Administration console and connect to the WSUS database on the export server.
2. In the WSUS Administration console, click **Synchronizations**. A list of the software updates synchronization attempts are displayed in the results pane.
3. In the results pane, find the latest software updates synchronization attempt and verify that it completed successfully.

Important

- The WSUSUtil tool must be run locally on the export server to export the software updates metadata, and it also must be run on the disconnected software update point server to import the software updates metadata. In addition, the user that runs the WSUSUtil tool must be a member of the local Administrators group on each server.
- If you are using Windows Server 2012, ensure [KB2819484](https://support.microsoft.com/help/2819484/cab-file-that-is-exported-by-using-the-wsusutil-exe-command-is-display) is installed on the WSUS servers.

## Export process for software updates

The export process for software updates consists of two main steps: to copy the locally stored license terms files to the disconnected software update point, and to export software updates metadata from the WSUS database on the export server.

Use the following procedure to copy the local license terms metadata to the disconnected software update point.

#### To copy local files from the export server to the disconnected software update point server

1. On the export server, navigate to the folder where software updates and the license terms for software updates are stored. By default, the WSUS server stores the files at &lt;*WSUSInstallationDrive*&gt;\WSUS\WSUSContent\, where *WSUSInstallationDrive* is the drive on which WSUS is installed.
2. Copy all files and folders from this location to the WSUSContent folder on the disconnected software update point server.

    Use the following procedure to export the software updates metadata from the WSUS database on the export server.

#### To export software updates metadata from the WSUS database on the export server

1. At the command prompt on the export server, navigate to the folder that contains WSUSutil.exe. By default, the tool is located at %*ProgramFiles*%\Update Services\Tools. For example, if the tool is located in the default location, type **cd %ProgramFiles%\Update Services\Tools**.
2. Type the following to export the software updates metadata to a package file:

    **wsusutil.exe export***packagename* *logfile*

    For example:

    **wsusutil.exe export export.xml.gz export.log**

    The format can be summarized as follows: WSUSutil.exe is followed by the export option, the name of the export .xml.gz file that is created during the export operation, and the name of a log file. WSUSutil.exe exports the metadata from the export server and creates a log file of the operation.

    Note

    The package (.xml.gz file) and the log file name must be unique in the current folder.
3. Move the export package to the folder that contains WSUSutil.exe on the import WSUS server.

    Note

    If you move the package to this folder, the import experience can be easier. You can move the package to any location that is accessible to the import server, and then specify the location when you run WSUSutil.exe.

## Import software updates metadata

Use the following procedure to import software updates metadata from the export server to the disconnected software update point.

Important

Never import any exported data from a source that you do not trust. If you import content from a source that you do not trust, it might compromise the security of your WSUS server.

#### To import metadata to the database of the import server

1. At the command prompt on the import WSUS server, navigate to the folder that contains WSUSutil.exe. By default, the tool is located at %*ProgramFiles*%\Update Services\Tools.
2. Type the following:

    **wsusutil.exe import***packagename* *logfile*

    For example:

    **wsusutil.exe import export.xml.gz import.log**

    The format can be summarized as follows: WSUSutil.exe is followed by the import command, the name of package file (.xml.gz) that is created during the export operation, the path to the package file if it is in a different folder, and the name of a log file. WSUSutil.exe imports the metadata from the export server and creates a log file of the operation.