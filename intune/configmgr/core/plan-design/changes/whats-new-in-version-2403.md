---
layout: Conceptual
title: What's new in version 2403 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2403
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
description: Get details about changes and new capabilities introduced in version 2403 of Configuration Manager current branch.
ms.date: 2024-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 0fab6ae9-e1a3-40e0-bfd3-15e5ce62d360
document_version_independent_id: 0fab6ae9-e1a3-40e0-bfd3-15e5ce62d360
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2403.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2403
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2403.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 9ca1c7c7-f036-4cfb-b702-d4f65e6eaa84
---

# What's new in version 2403 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2403 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2211 or later. When installing a new site, it will also be available as a [baseline version](../../servers/manage/updates#bkmk_note1) soon after global availability. This article summarizes the changes and new features in Configuration Manager, version 2403.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2403](../../servers/manage/checklist-for-installing-update-2403). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2403#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Site infrastructure

### Microsoft Azure Active Directory rebranded to Microsoft Entra ID

Starting Configuration Manager version 2403, Microsoft Azure Active Directory is renamed to Microsoft Entra ID within Configuration Manager.

For more information, see [New name for Azure Active Directory](/en-us/entra/fundamentals/new-name).

### Automated diagnostic Dashboard for Software Update Issues

A new dashboard is added to the console under monitoring workspace, which shows the diagnosis of the software update issues in your environment this feature can easily identify any issues related to software updates. You can fix software update issues based on troubleshooting documentations.

![Screenshot of new troubleshooting dashboard in console.](media/17668422-troubleshooting-dash.png)

For more information, see [Software update health dashboard.](../../clients/manage/software-update-health-dashboard)

### Introducing centralized search box: Effortlessly find what you need in the console!

Users can now use the global search box in CM console, which streamlines the search experience and centralizes access to information. This feature enhances the overall usability, productivity and effectiveness of CM. Users no longer need to navigate through multiple nodes or sections/ folders to find information they require, saving valuable time and effort.

![Screenshot of centralized search box in console.](media/24501008-search-box.png)

For more information, see [Improvements to console search.](../../servers/manage/admin-console-tips#improvements-to-console-search)

### Added Folder support for Scripts node in Software Library

You can now organize scripts by using folders. This change allows for better categorization and management of scripts. Full Administrator and Operations Administrator roles can manage the folders.

![Screenshot of scripts folder structure in console.](media/24475159-folder-scripts.png)

For more information, see [Folder support for scripts.](../../../apps/deploy-use/create-deploy-scripts#folder-support-for-scripts)

### HTTPS or Enhanced HTTP should be enabled for client communication from this version of Configuration Manager

HTTP-only communication is deprecated, and support is removed from this version of Configuration Manager. Enable HTTPS or Enhanced HTTP for client communication.

For more information, see [Enable site system roles for HTTPS or Enhanced HTTP.](../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http) and [Deprecated features](deprecated/removed-and-deprecated-cmfeatures)

### Windows Server 2012/2012 R2 operating system site system roles are not supported from this version of Configuration Manager

Starting 2403, Windows Server 2012/2012 R2 operating system site system roles aren't supported in any CB releases. Clients with extended support (ESU) will continue to support.

For more information, see [Supported-operating-systems-for-site-system-servers.](../configs/supported-operating-systems-for-site-system-servers)

### Resource access profiles and deployments will block Configuration manager upgrade

Any configured Resource access profiles and deployments block Configuration manager upgrade. Consider deleting them and moving the co-management workload for Resource Access (if co-managed) to Intune.

For more information, see [FAQ](../../../protect/plan-design/resource-access-deprecation-faq) and [Resource access policies are no longer supported.](../../servers/deploy/install/list-of-prerequisite-checks)

## Software updates

### New parameter SoftwareUpdateO365Language is added to Save-CMSoftwareUpdate cmdlet

A new parameter **SoftwareUpdateO365Language** is now added to PowerShell Save-CMSoftwareUpdate cmdlet. Customers now don't have to check a specific language in the SUP Properties (causing a metadata download for that language for all updates).

PowerShell Commandlet: `Save-CMSoftwareUpdate – SoftwareUpdateO365Language <language name> (<region name>)"`

Note

Languages need to be in O365 format to be consistent with Admin Console UI. E.g. "Hungarian (Hungary)".

## OS deployment

### Support for ARM 64 Operating System Deployment

Configuration Manager operating system deployment support is now added on Windows 11 ARM 64 devices. Currently Importing and customizing Arm 64 boot images, Wipe and load TS, Media creation TS, WDS PXE for Arm 64 and CMPivot is supported.

![Screenshot of arm 64 boot image in console.](media/14959666-armosd.png)

### Enhancement in Deploying Software Packages with Dynamic Variables

When deploying a Task Sequence for installing a software package using dynamic variables, if the 'Continue on error' option is unchecked and the package is updated on distribution points while the client is installing the Task Sequence, the installation process fails due to version inconsistencies with the updated packages on the distribution points. Previously, the only recourse was to reinstall the entire Task Sequence from the software center.

To address this issue, we've introduced a new feature allowing administrators to specify the number of retries the system should attempt before marking the Task Sequence as failed. This retry mechanism is activated only when the 'Continue on error' checkbox is unchecked."

![Screenshot of changes in dynamic variable in task sequence in CM console.](media/24334765-dyn-var.png)

For more information, see [Options for Install Application.](../../../osd/understand/task-sequence-steps#retry-this-step-if-computer-unexpectedly-restarts)

## Cloud-attached management

### Upgrade to CM 2403 is blocked if CMG V1 is running as a cloud service (classic)

The option to upgrade Configuration Manager 2403 is blocked if you're running cloud management gateway V1 (CMG) as a cloud service (classic). All CMG deployments should use a virtual machine scale set.

For more information, see [Check for a cloud management gateway (CMG) as a cloud service (classic).](../../servers/deploy/install/list-of-prerequisite-checks)

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

- System Center Update Publisher (SCUP) and integration with ConfigMgr planned end of support Jan 2024.

For more information, see [Removed and deprecated features for Configuration Manager.](deprecated/removed-and-deprecated-cmfeatures).

## Other updates

#### Improvements to Bitlocker

This release includes the following improvements to Bitlocker:

- Starting in this release, this feature ensures proper verification of key escrow and prevents message drops. We now validate whether the key is successfully escrowed to the database, and only on successful escrow we add the key protector.
- This feature now prevents a potential data loss scenario where BitLocker is protecting the volumes with keys that are never backed up to the database, in any failures to escrow happens.

For more information on BitLocker management, see [Deploy BitLocker management.](../../../protect/deploy-use/bitlocker/recovery-service) and [Plan for BitLocker management.](../../../protect/plan-design/bitlocker-management).

- From this version of Configuration Manager, the Windows 11 readiness dashboard shows charts for Windows 23H2.
- Defender Exploit Guards policy for controlled folder now accepts regex in the file path for apps. For example, [C:\Folder\Subfolder\app?.exe] [C:\Folder1\Sub\*Name]