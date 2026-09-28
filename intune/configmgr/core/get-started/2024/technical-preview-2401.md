---
layout: Conceptual
title: Technical preview 2401 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2024/technical-preview-2401
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2401.
ms.date: 2024-01-24T00:00:00.0000000Z
ms.topic: whats-new
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: tier3
locale: en-us
document_id: adee2517-be0d-47f7-9937-9549090bdd1b
document_version_independent_id: adee2517-be0d-47f7-9937-9549090bdd1b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2024/technical-preview-2401.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2024/technical-preview-2401
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2024/technical-preview-2401.md
platformId: 1b946c56-eb5f-124b-6370-5d1e6560946f
---

# Technical preview 2401 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2401. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Automated diagnostic Dashboard for Software Update Issues

A new dashboard is added to the console under monitoring workspace which shows the diagnosis of the software update issues in your environment. You can fix software update issues based on CM troubleshooting documentation.

![Screenshot of new troubleshooting dashboard in console.](media/17668422-troubleshoot-dash.png)

## Introducing Centralized Search box: Effortlessly Find What You Need in the Console!

Users can now use the global search box in CM console which streamlines the search experience and centralizes access to information. This enhances the overall usability, productivity and effectiveness of CM. Users no longer need to navigate through multiple nodes or sections/ folders to find information they require, saving valuable time and effort.

![Screenshot of centralized search box in console.](media/24501008-search-box.png)

## Microsoft Azure Active Directory rebranded to Microsoft Entra ID

Starting Configuration Manager version 2403, Microsoft Azure Active Directory is renamed to Microsoft Entra ID within Configuration Manager.

## Enhancement in Deploying Software Packages with Dynamic Variables

With the introduction of retry count in UI administrators while deploying the "Install Software Package" via Dynamic variable with "Continue on error" unchecked to clients, won't be notified with task sequence failures even if package versions on the distribution point are updated.

![Screenshot of changes in dynamic variable in task sequence in CM console.](media/24334765-dyn-var.png)

## Enabling Auto-Image Patching for CMG Virtual Machine Scale Set

With this version of CM Configuration Manager Cloud Management Gateway (CMG) Virtual Machine Scale introduces enabling of Auto-Image Patching for seamless and automated updates to ensure your environment stays current and secure with this efficient solution.

## Window 11 Readiness dashboard to support Windows 23H2

With this version of Configuration Manager, the Windows 11 readiness dashboard will show charts for Windows 23H2.

## HTTPS or Enhanced HTTP should be enabled for client communication from this version of Configuration Manager

HTTP-only communication is deprecated, and support is removed from this version of Configuration Manager. Please enable HTTPS or Enhanced HTTP for client communication.

![Screenshot of HTTPS new option in console.](media/25601199-http-dep.png)

## Upgrade to CM 2403 is blocked if CMG V1 is running as a cloud service (classic)

The option to upgrade Configuration Manager 2403 is blocked if you're running cloud management gateway V1 (CMG) as a cloud service (classic).All CMG deployments should use a virtual machine scale set.

## Windows Server 2012/2012 R2 operating system site system roles aren't supported from this version of Configuration Manager

Starting 2403, Windows Server 2012/2012 R2 operating system site system roles aren't supported in any CB releases.

## Improvements to Bitlocker

This release includes the following improvements to Bitlocker:

- Based on your feedback, this feature ensures proper verification of key escrow and prevents message drops. We now validate whether the key is successfully escrowed to the database, and only on successful escrow we add the key protector.
- This feature prevents a potential data loss scenario where BitLocker is protecting the volumes with keys that are never backed up to the database, in any failures to escrow happens.

## General known issues

Upgrading from TP 2311 to 2401 may encounter a prereq check failure if the Resource Access slider is already in Intune. This regression is caused by the previous TP. To resolve this issue, follow these steps:

- Move any other slider (Apps/Endpoint) to Configuration Manager (CM) or Intune.
- Choose to apply the changes and click 'Ok.'
- Proceed with upgrading the site to TP 2401.
- Once the upgrade is complete, you can revert the (Apps/Endpoint) slider back to its old settings."