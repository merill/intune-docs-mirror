---
layout: Conceptual
title: Scenarios to deploy enterprise operating systems - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems
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
description: Learn about several scenarios to deploy enterprise operating systems with Configuration Manager.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 7b9f42a9-1991-cc9e-ee70-0bbaa85d0dc3
document_version_independent_id: 66efebc4-0b35-61c8-ac69-a5daaeaeb372
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 81a74c9d-4d51-ad7d-6e08-22bd795e2c0c
---

# Scenarios to deploy enterprise operating systems - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The following OS deployment scenarios are available in Configuration Manager:

## Upgrade Windows to the latest version

This scenario upgrades the OS on computers that run an earlier version of Windows. The upgrade process keeps the applications, settings, and user data on the computer. There are no external dependencies, such as the Windows ADK. This process can be faster and more resilient than traditional OS deployments.

This scenario applies to all [supported versions](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices) of Windows client and Windows Server.

For more information, see [Upgrade Windows to the latest version](upgrade-windows-to-the-latest-version).

## Windows Autopilot for existing devices

Windows Autopilot for existing devices is available with Windows 10, version 1809 or later. This feature allows you to reimage and provision a device with an earlier version of Windows for Windows Autopilot user-driven mode using a single Configuration Manager task sequence.

This scenario applies to Windows 10 version 1809 and later

For more information, see [Windows Autopilot for existing devices](/en-us/autopilot/existing-devices).

## Refresh an existing computer with a new version

This scenario partitions and formats an existing computer and installs a new OS on the computer. It's also referred to as *wipe and load*. You can migrate settings and user data after the OS is installed.

This scenario applies to all [supported versions](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices) of Windows client and Windows Server.

For more information, see [Refresh an existing computer with a new version of Windows](refresh-an-existing-computer-with-a-new-version-of-windows).

## Install a new version of Windows on a new computer

This scenario installs an OS on a new computer. It's also referred to as *bare metal*. It's a fresh installation of the OS and doesn't include any settings or user data migration.

This scenario applies to all [supported versions](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices) of Windows client and Windows Server.

For more information, see [Install a new version of Windows on a new computer (bare metal)](install-new-windows-version-new-computer-bare-metal).

## Replace an existing computer and transfer settings

This scenario installs an OS on a new computer, and migrates settings and user data from an old computer to the new computer.

This scenario applies to all [supported versions](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices) of Windows client and Windows Server.

For more information, see [Replace an existing computer and transfer settings](replace-an-existing-computer-and-transfer-settings).