---
layout: Conceptual
title: Technical preview releases - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview
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
description: Learn about the technical preview branch to test-drive new functionality and capabilities in Configuration Manager.
ms.date: 2024-11-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 219f74c9-4a13-a482-f0c3-5d44793fcd7c
document_version_independent_id: 3e6b34b6-ee13-4dba-79af-4d49e4461e89
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/technical-preview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/technical-preview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/technical-preview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 982ae491-164d-c700-a097-5f8210e8f057
---

# Technical preview releases - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article provides details about the monthly technical preview branch of Configuration Manager. The technical preview introduces new functionality that Microsoft is working on. It introduces new features that aren't yet included in the current branch of Configuration Manager. These features might eventually be included in an update to the current branch. Before we finalize the features, we want you to try them out and give us feedback.

Because this release is a technical preview, details and functionality are subject to change.

This information applies to all versions of the Configuration Manager technical preview branch. This article lists each new feature along with the technical preview version in which it first appears. For example, version **2201** for January (`01`) of 2022 (`22`). Separate articles dedicated to each preview version detail the individual features.

For information about what's new in the *current branch* of Configuration Manager, see [What's new in Configuration Manager incremental versions](../plan-design/changes/whats-new-incremental-versions).

Tip

You can use RSS to be notified when this page is updated. For more information, see [How to use the docs](../../../fundamentals/use-docs#notifications).

## Requirements and limitations

Important

The technical preview is licensed for use only in a lab environment. Microsoft may not provide support services and certain features may not be available in technical previews. Additionally, technical preview software may have reduced or different security, privacy, accessibility, availability, and reliability standards relative to commercially provided software.

For most product prerequisites, use the information in the [Supported configurations](../plan-design/configs/supported-configurations). The following exceptions apply to the technical preview branch:

- Each install is active for 360 days before it becomes inactive.
- English is the only language supported.
- It only supports the following setup command-line parameters:

    - `/silent`
    - `/testdbupgrade`
- The service connection point installs to online mode. It doesn't support offline mode.

    Note

    You may need to allow specific internet URLs, some of which are specific to the technical preview branch. For more information, see [Internet access requirements](../plan-design/network/internet-endpoints).
- The separate articles for each specific version of the technical preview include additional limitations or requirements, as applicable.
- The following features aren't supported with the technical preview branch:

    - [Migration](../migration/migrate-data-between-hierarchies) to or from this preview branch.
    - [Upgrade](../servers/deploy/install/upgrade-to-configuration-manager) to this preview branch.
    - [Site recovery](../servers/manage/recover-sites) from the cd.latest folder.
- There's no support for updating to current branch from this preview branch.

    Note

    When updates are available for a preview version, you still find and install them from the **Updates and Servicing** node of the Configuration Manager console. For a video of the in-console upgrade process, see [Installing Configuration Manager update packages](https://www.youtube.com/embed/KBd_EGFbUT8) on youtube.com.
- It only supports a standalone primary site. There's no support for a central administration site, multiple primary sites, or secondary sites.

The technical preview branch of Configuration Manager supports the following products and technologies:

- Unless otherwise noted, the technical preview branch supports the same versions of SQL Server as the current branch. For more information, see [Supported SQL Server versions](../plan-design/configs/support-for-sql-server-versions).
- The site supports up to 10 clients, which can run any [supported client OS version](../plan-design/configs/supported-operating-systems-for-clients-and-devices).

Note

The inclusion of these products in this content doesn't imply an extension of support for a version that's beyond its support lifecycle. Configuration Manager doesn't support products that are beyond their support lifecycle. For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/lifecycle).

## Install and update

The Configuration Manager technical preview branch for lab use is distinct from the Configuration Manager current branch for production use.

First install a baseline version of the technical preview branch. After installing a baseline version, then use in-console updates to bring your installation up to date with the most recent preview version. Typically, new versions of the technical preview are available each month.

Microsoft supports each technical preview version up until three successive versions are available. For example, when version 1908 released, version 1904 was no longer in support. Versions 1905, 1906, and 1907 remained in support. When a baseline falls out of support, it's still supported for installing a new technical preview site, assuming you immediately update to a supported version. The older baseline is supported until a new baseline version is available. Update to the latest available version from the baseline, and then repeat the update process until you install the latest technical preview version.

Tip

When you install an update to the technical preview, you update your preview installation to that new technical preview version. A technical preview installation never has the option to upgrade to a current branch installation. It also never receives updates from the current branch release.

Several times throughout the year, there are technical preview branch and current branch versions with the same version number. For example, there is a technical preview version 2006 and a current branch version 2006.

### Active baseline versions

Install a baseline version for up to one year after its release. When you install a new technical preview site, use the latest baseline version:

- **Technical preview version 2411**

Download a baseline version from the [Evaluation Center](https://www.microsoft.com/en-in/evalcenter/evaluate-microsoft-endpoint-configuration-manager-technical-preview).

## Providing feedback

We love to hear your feedback about the new features in the technical preview. For more information, see [Product feedback](../understand/product-feedback).

If you have ideas about new features you would like to see, let us know! Submit new ideas and vote on the ideas by others: [Feedback for Configuration Manager](https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472).

## Features in the most recent version

The following features are available with the most recent Configuration Manager technical preview version:

### Technical preview version 2411

- [Operating System support added for Windows 11 24H2 and Windows Server 2025](2024/technical-preview-2411)
- [Enhanced Security for CMG](2024/technical-preview-2411)
- [SQL 2012 and 2014 support is deprecated](2024/technical-preview-2411)
- [Software metering support in Arm64 devices](2024/technical-preview-2411)

Note

Features that were available in a previous version of the technical preview remain available in later versions. Similarly, features that are added to the Configuration Manager current branch remain available in the technical preview branch.

## Features in recent technical previews

The following features were released with previous versions of the Configuration Manager technical preview branch since the latest current branch version:

Tip

When a new current branch version is available, features that are available in that version are listed in the latest *What's new* article. For more information, see [What's new in incremental versions](../plan-design/changes/whats-new-incremental-versions#supported-versions).

### Technical preview version 2405

- [Introducing Centralized Search - Desired Workspace Selection](2024/technical-preview-2405)
- [BitLocker support in Arm devices](2024/technical-preview-2405)
- [Configuration Manager now support SQL Extended Protection for Authentication](2024/technical-preview-2405)
- [Performance Enhancement of policy processing and collection evaluation](2024/technical-preview-2405)

Note

Features that were available in a previous version of the technical preview remain available in later versions. Similarly, features that are added to the Configuration Manager current branch remain available in the technical preview branch.

### Technical preview version 2401

- [Automated diagnostic Dashboard for Software Update Issues](2024/technical-preview-2401)
- [Introducing Centralized Search box: Effortlessly Find What You Need in the Console!](2024/technical-preview-2401)
- [HTTPS or Enhanced HTTP should be enabled for client communication from this version of Configuration Manager](2024/technical-preview-2401)
- [Microsoft Azure Active Directory re-branded to Microsoft Entra ID](2024/technical-preview-2401)
- [Enhancement in Deploying Software Packages with Dynamic Variables](2024/technical-preview-2401)
- [Enabling Auto-Image Patching for CMG Virtual Machine Scale Sets](2024/technical-preview-2401)
- [Window 11 Readiness dashboard to support Windows 23H2](2024/technical-preview-2401)
- [Windows Server 2012/2012 R2 operating system site system roles are not supported from this version of Configuration Manager](2024/technical-preview-2401)
- [Upgrade to CM 2403 is blocked if CMG V1 is running as a cloud service (classic)](2024/technical-preview-2401)
- [Improvements to Bitlocker](2024/technical-preview-2401)

### Technical preview version 2311

- [Folder support for Scripts node in Software Library](2023/technical-preview-2311)
- [New parameter SoftwareUpdateO365Language is added to Save-CMSoftwareUpdate cmdlet](2023/technical-preview-2311)
- [Support for ARM64 Operating System Deployment](2023/technical-preview-2311)
- [Resource access profiles and deployments will block Configuration manager upgrade](2023/technical-preview-2311)
- [WildCard Support added in Defender Exploit Guard policy for Controlled Folders](2023/technical-preview-2311)

### Technical preview version 2307

- [Windows 11 Edition Upgrade using Configuration Manager policy settings](2023/technical-preview-2307)
- [Windows 11 Upgrade Readiness Dashboard](2023/technical-preview-2307)
- [Option to schedule scripts' runtime](2023/technical-preview-2307)
- [External service notification Run details from Azure Logic application](2023/technical-preview-2307)
- [Maintenance window creation using PS cmdlet](2023/technical-preview-2307)
- [Update Orchestrator Service (USO) for Windows 11 22H2 or later with windows native reboot experience](2023/technical-preview-2307)

### Technical preview version 2305

- [OSD preferred MP option for PXE boot scenario](2023/technical-preview-2305)
- [New Site Maintenance task "Delete Aged Task Execution Status Messages" is now available on primary servers to cleanup data older than 30 days or configured number of days](2023/technical-preview-2305)
- [CMG creation using 3rd PartyApp via Console](2023/technical-preview-2305)
- [CMG creation using 3rd Party ServerApp via PowerShell](2023/technical-preview-2305)
- [Attack Surface Reduction (ASR) capability now marks Server SKU as compliant only after enforcement](2023/technical-preview-2305)
- [Enhancing security for External service notifications URL](2023/technical-preview-2305)
- [Enable Bitlocker through ProvisionTS](2023/technical-preview-2305)
- [Client certificate state in console (self-signed) to match state in control panel(PKI)](2023/technical-preview-2305)

### Technical preview version 2303

- [SQL Server 2022 version support added for Configuration Manager](2023/technical-preview-2303#bkmk_SQlodbc)
- [Dark theme extended to one customer voice (OCV) wizard](2023/technical-preview-2303#bkmk_dark)
- [Prerequisites for the site server roles now include ODBC driver for SQL Server](2023/technical-preview-2303#bkmk_SQl2022)

### Technical preview version 2302

- [Dark theme extended to delete secondary site wizard](2023/technical-preview-2302#bkmk_dark)
- [Enable Windows features introduced via Windows servicing that are off by default](2023/technical-preview-2302#bkmk_winfeatures)

### Technical preview version 2301

- [Removing Microsoft Store for Business and Education new config capability](2023/technical-preview-2301#bkmk_msfb)
- [Update to the default value of supersedence age in months for software updates](2023/technical-preview-2301#bkmk_softwareupdates)
- [Microsoft Configuration Manager product branding](2023/technical-preview-2301#bkmk_branding)
- [Improvements to Cloud Sync (Collections to Microsoft Entra group Synchronization) feature](2023/technical-preview-2301#bkmk_coll_aad_group_sync)

### Technical preview version 2211

- [Authorization failure message in admin service now shown in Status message viewer](2022/technical-preview-2211#bkmk_audit-admin-service)
- [Network Access Account (NAA) account usage alert](2022/technical-preview-2211#bkmk_naa-account)
- [Improvements to Cloud Sync (Collections to Microsoft Entra group Synchronization) feature](2022/technical-preview-2211#bkmk_coll_aad_group_sync)

### Technical preview version 2210

- [Featured Apps in Software Center](2022/technical-preview-2210#bkmk_featured-apps-software-center)

### Technical preview version 2209

- [Improvements to the console](2022/technical-preview-2209#bkmk_improvements-to-the-console)
- [Improvements to the dark theme](2022/technical-preview-2209#bkmk_improvements-to-the-dark-theme)
- [Other Updates](2022/technical-preview-2209#bkmk_other-updates)

### Technical preview version 2208

- [Intune RBAC for tenant attached devices](2022/technical-preview-2208#bkmk_enable-intune)
- [Dark theme is now extended to additional dashboards](2022/technical-preview-2208#bkmk_improvements-to-the-dark-theme)

### Technical preview version 2207

- [Distribution point content migration](2022/technical-preview-2207#bkmk_dpconmig)
- [Improvements to Configuration Manager policies for Microsoft Defender Application Guard](2022/technical-preview-2207#bkmk_app-guard)
- [PowerShell release notes preview](2022/technical-preview-2207#bkmk_powershell)

### Technical preview version 2206

- [Default site boundary group behavior to support cloud source selection](2022/technical-preview-2206#bkmk_dbgmp)
- [PowerShell release notes preview](2022/technical-preview-2206#bkmk_powershell)

### Technical preview version 2205

- [Offset for reoccurring monthly maintenance window schedules](2022/technical-preview-2205#bkmk_offset)
- [Improvements to cloud management gateway (CMG) workflow](2022/technical-preview-2205#bkmk_cmg)
- [Script execution timeout for compliance settings](2022/technical-preview-2205#bkmk_timeout)
- [Microsoft Defender for Endpoint onboarding for Windows Server 2012 R2 and Windows Server 2016](2022/technical-preview-2205#bkmk_downlevel)
- [PowerShell release notes preview](2022/technical-preview-2205#bkmk_powershell)

### Technical preview version 2204

- [Administration Service Management option](2022/technical-preview-2204#bkmk_administration)
- [Folders for automatic deployment rules (ADRs)](2022/technical-preview-2204#bkmk_folder)

### Technical preview version 2203

- [Dark theme for the console](2022/technical-preview-2203#bkmk_dark)
- [Escrow BitLocker recovery password to the site during a task sequence](2022/technical-preview-2203#bkmk_blmts)
- [PowerShell release notes preview](2022/technical-preview-2203#bkmk_powershell)

### Technical preview version 2202

- [Delete collection references](2022/technical-preview-2202#bkmk_delcollref)
- [Pre-download content for available software updates](2022/technical-preview-2202#bkmk_pre-download)
- [Added folder support for nodes in the Software Library](2022/technical-preview-2202#bkmk_folder)
- [New client health checks](2022/technical-preview-2202#bkmk_health)
- [Improvements to implicit uninstall](2022/technical-preview-2202#bkmk_implicit)
- [Improvements for sending feedback](2022/technical-preview-2202#bkmk_feedback)
- [Improvements to Management Insights](2022/technical-preview-2202#bkmk_insights)
- [Improvements to dashboards](2022/technical-preview-2202#bkmk_webview2)
- [ADR scheduling improvements for deployments](2022/technical-preview-2202#bkmk_adr)
- [Console improvements](2022/technical-preview-2202#bkmk_console)
- [PowerShell release notes preview](2022/technical-preview-2202#bkmk_powershell)