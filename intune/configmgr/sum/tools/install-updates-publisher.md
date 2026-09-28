---
layout: Conceptual
title: Install Updates Publisher - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/install-updates-publisher
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
description: Install System Center Updates Publisher in your environment
ms.date: 2021-10-20T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 3dee329b-0e2f-5e5d-877c-ad093987be90
document_version_independent_id: 53b40201-cc55-137c-3ad7-3d524176ba29
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/tools/install-updates-publisher.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/tools/install-updates-publisher
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/tools/install-updates-publisher.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 30bea517-c287-b3d8-a191-6a0943f9d0cf
---

# Install Updates Publisher - Configuration Manager | Microsoft Learn

*Applies to: System Center Updates Publisher*

The information in these articles can help you download, install, and set up Updates Publisher for use with your Configuration Manager environment.

## Prerequisites and limitations

System Center Updates Publisher can only be used with Configuration Manager. It isn't intended for use with stand-alone WSUS hierarchies.

The following sections detail requirements to install and use Updates Publisher, and limitations or known issues for its use.

### Operating systems

Install and run Updates Publisher on a 64-bit editions of the following operating systems. There are no minimum cumulative update or service pack requirements.

- Windows Server 2016 (Standard, Datacenter)
- Windows Server 2012 R2 (Standard, Datacenter)
- Windows 11
- Windows 10 (Pro, Education, Pro Education, Enterprise)
- Windows 8.1 (Professional, Enterprise)

### Prerequisites

The following are required on the computer that runs Updates Publisher.

- **64-bit operating system**: The computer where you install Updates Publisher must run a 64-bit operating system.
- **WSUS 6.2 or later**:
    - On Windows Server, install the default Administration Console to meet this requirement.
    - For Windows 8.1 or later operating systems, install the [Remote Server Administration Tools (RSAT) for Windows operating systems](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems). This installs the necessary support to use Updates Publisher (*API and PowerShell cmdlets*, and *User Interface Management Console*).
- **Permissions**:
    - Installation: Local admin
    - Most operations: local user
    - Publishing, or operations that involve WSUS: Member of WSUS Administrators group on the WSUS Server.

### Supported languages

Updates Publisher is available only in English but can manage updates for other languages. The language support depends on the task, such as publishing, creating, or editing updates.

When exporting or publishing updates, Updates Publisher displays the title and description of the software update based on the locale of the computer where Updates Publisher is installed.

For example, you create a software update that has an English and Spanish title.

- If you create the update on a computer whose locale is English, by default, you would see the title and description in English.
- If you then export or publish that update to a computer whose locale is Spanish, on that computer you would see the title and description in Spanish.

### Publishing

When you publish software updates, you can specify the language of the software update binary file. You can also specify that the binary is language neutral. The following languages are supported:

- Arabic
- Chinese (Hong Kong S.A.R.)
- Chinese (Traditional)
- Chinese (Simplified)
- Czech
- Danish
- Dutch
- English
- Finnish
- French
- German
- Greek
- Hebrew
- Hungarian
- Italian
- Japanese
- Korean
- Norwegian
- Polish
- Portuguese
- Portuguese (Brazil)
- Russian
- Spanish
- Swedish
- Turkish

### Software update titles and descriptions

The following languages are supported for software update titles and descriptions.

- Chinese (Traditional)
- Chinese (Simplified)
- English
- French
- German
- Italian
- Japanese
- Korean
- Portuguese (Brazil)
- Russian
- Spanish

## Install Updates Publisher

Get the **UpdatesPubliser.msi** for installing System Center Updates Publisher from https://aka.ms/SCUPDownload.

To install Updates Publisher, run **UpdatesPublisher.msi** on a computer that meets the *prerequisites*. The installer creates the following folder to contain the files necessary to run Updates Publisher: %PROGRAMFILES%\Microsoft\UpdatesPublisher\*.

Because this folder contains all the files necessary to use Updates Publisher, you can copy the folder and its contents to a new location or computer and then use Updates Publisher from that location. However, the new location or computer must meet the prerequisites to run Updates Publisher.

After installation completes, run **UpdatesPublisher.exe** from the *UpdatesPublisher* folder to start Updates Publisher.