---
layout: Conceptual
title: Planning client deployment to Mac computers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-mac-computers
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
description: Plan for client deployment to Mac computers in Configuration Manager.
ms.date: 2022-01-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 4ef131fa-c92c-cc72-2e36-b46909e4a2e5
document_version_independent_id: 47049aa7-26e4-c604-ceb6-ad0157772be6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-mac-computers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-mac-computers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-mac-computers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: cdac3d90-3a77-27f9-e062-3073d9cc9a9e
---

# Planning client deployment to Mac computers - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in January 2022, this feature of Configuration Manager is deprecated. For more information, see [Mac computers](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers).

You can install the Configuration Manager client on Mac computers that run macOS X and use the following management capabilities:

- **Hardware inventory**

    You can use Configuration Manager hardware inventory to collect information about the hardware and installed applications on Mac computers. This information can then be viewed in Resource Explorer in the Configuration Manager console and used to create collections, queries and reports. For more information, see [How to use Resource Explorer to view hardware inventory](../../manage/inventory/use-resource-explorer-to-view-hardware-inventory).

    Configuration Manager collects the following hardware information from Mac computers:

    - Processor
    - Computer System
    - Disk Drive
    - Disk Partition
    - Network Adapter
    - Operating System
    - Service
    - Process
    - Installed Software
    - Computer System Product
    - USB Controller
    - USB Device
    - CDROM Drive
    - Video Controller
    - Desktop Monitor
    - Portable Battery
    - Physical Memory
    - Printer

    Important

    You cannot extend the hardware information that is collected from Mac computers during hardware inventory.
- **Compliance settings**

    You can use Configuration Manager compliance settings to view the compliance of and remediate macOS X preference (.plist) settings. For example, you could enforce settings for the home page in the Safari web browser or ensure that the Apple firewall is enabled. You can also use shell scripts to monitor and remediate settings in macOS X.
- **Application management**

    Configuration Manager can deploy software to Mac computers. You can deploy the following software formats to Mac computers:

    - Apple disk image (.DMG)
    - Meta package file (.MPKG)
    - macOS X installer package (.PKG)
    - macOS X application (.APP)

    When you install the Configuration Manager client on Mac computers, you cannot use the following management capabilities that are supported by the Configuration Manager client on Windows-based computers:
- Client push installation
- Operating system deployment
- Software updates

    Note

    You can use Configuration Manager application management to deploy required macOS X software updates to Mac computers. In addition, you can use compliance settings to make sure that computers have any required software updates.
- Maintenance windows
- Remote control
- Power management
- Client status client check and remediation

    For more information about how to install and configure the Configuration Manager Mac client, see [How to deploy clients to Macs](../deploy-clients-to-macs).