---
layout: Conceptual
title: New version 1710 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-1710
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
description: Get details about changes and new capabilities introduced in version 1710 of Configuration Manager.
ms.date: 2018-01-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: c70c8bc8-b49b-86d8-0152-041c18cb4216
document_version_independent_id: f4b148e0-2387-34da-7167-ade1c73b4a00
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-1710.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-1710
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-1710.md
platformId: 9a14b2d8-93ca-5249-f350-3ccda9b657c9
---

# New version 1710 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 1710 for Configuration Manager current branch is available as an in-console update for previously installed sites that run version 1610, 1702, or 1706.

Aside from new features, this release also includes additional changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 1710](https://support.microsoft.com/help/4056470/summary-of-changes-in-system-center-configuration-manager-current-bran).

The following additional updates to this release are also now available:

- [Update rollup for Configuration Manager current branch, version 1710](https://support.microsoft.com/help/4057517/update-rollup-for-system-center-configuration-manager-current-branch-v)
- [Update rollup 2 for Configuration Manager current branch, version 1710](https://support.microsoft.com/en-us/help/4086143/update-rollup-2-for-system-center-configuration-manager-current-branch)

Tip

To install a new site, you must use a baseline version of Configuration Manager.

Learn more about:

- [Installing new sites](../../servers/deploy/install/installing-sites)
- [Installing updates at sites](../../servers/manage/updates)
- [Baseline and update versions](../../servers/manage/updates#bkmk_Baselines)

The following sections provide details about changes and new capabilities introduced in version 1710 of Configuration Manager.

## Site infrastructure

### Updates for Peer Cache

Beginning with this release, Peer Cache is no longer a pre-release feature. No other changes for Peer Cache are introduced with this release. For more information, see [Peer Cache for Configuration Manager clients](../hierarchy/client-peer-cache).

### Cloud distribution point support for Azure Government Cloud

You can now use [cloud-based distribution points](/en-us/previous-versions/troubleshoot/configmgr/use-a-cloud-based-distribution-point) in the Azure Government cloud.

### Inventory default unit revision

As devices now include hard drives with sizes in the gigabyte (GB), terabyte (TB) and larger scales, this release changes the default unit (SMS\_Units) used in many views from megabytes (MB) to GB. For example, the v\_gs\_LogicalDisk.FreeSpace value now reports GB units.

## Client management

### Co-management for Windows 10 devices

In the previous Windows 10 updates, you can already join a Windows 10 device to on-premises Active Directory (AD) and cloud-based Azure AD at the same time (hybrid Azure AD). Starting with Configuration Manager version 1710, co-management takes advantage of this improvement and enables you to concurrently manage Windows 10, version 1709 (also known as the Fall Creators Update) devices by using both Configuration Manager and Intune. It's a solution that provides a bridge from traditional to modern management and gives you a path to make the transition using a phased approach. For details, see [Co-management for Windows 10 devices](../../../comanage/overview).

### Restart computers from the Configuration Manager console

Beginning with this release, you can use the Configuration Manager console to identify client devices that require a restart, and then use a client notification action to restart them.

See [How to manage clients](../../clients/manage/manage-clients#restart-clients)

## Application Management

### Improvements for Run Scripts

This release brings several improvements to the **Run Scripts** feature, which lets you deploy PowerShell scripts to run on managed devices. This feature was first introduced in version 1706.

Improvements include:

- Use Security Scopes to help control who can use Run Scripts
- Real-time monitoring of the scripts you run
- Parameters for the script display in Create Script Wizard, support validation, and are identified as mandatory or optional.

For more on using Run Scripts, see [Create and run scripts](../../../apps/deploy-use/create-deploy-scripts).

### New mobile application management policy settings

The following settings have been added to the mobile application management policy settings:

- **Disable contact sync**: Prevents the app from saving data to the native Contacts app on the device.
- **Disable printing**: Prevents the app from printing work or school data.

### Software Center no longer distorts icons larger than 250x250

With this release, Software Center will no longer distort icons that are larger than 250x250. Software Center made such icons look blurry. You can now set an icon with a pixel dimensions of up to 512x512, and it displays without distortion.

To add an icon for your app in Software Center, see [Create applications](../../../apps/deploy-use/create-applications).

## Operating system deployment

Tip

Beginning with the Windows 10, version 1709 (also known as the Fall Creators Update) release, Windows media includes multiple editions. When configuring a task sequence to use an operating system upgrade package or operating system image, be sure to select an [edition that is supported for use by Configuration Manager](../configs/support-for-windows-10).

### Add child task sequences to a task sequence

You can add a new task sequence step that runs another task sequence, which creates a parent/child relationship between the task sequences. This allows you to create more modular task sequences that you can re-use.

To learn more about the child task sequence, see [Child task sequence](../../../osd/understand/task-sequence-steps#child-task-sequence).

## Software Center customization

You can add enterprise branding elements and specify the visibility of tabs on Software Center. You can add your Software Center specific company name, set a Software Center configuration color theme, set a company logo, and set the visible tabs for client devices.

For more information, see [Plan for and configure application management](../../../apps/plan-design/plan-for-and-configure-application-management).

## Software updates

### Surface driver updates

Beginning with this release, managing Surface driver updates is no longer a pre-release feature.

## Reporting

### Limit Windows 10 Enhanced data to only send data relevant to Windows Analytics Device Health

You can now set the Windows 10 diagnostic data collection level to **Enhanced (Limited)**. This setting enables you to gain actionable insight about devices in your environment without devices reporting all of the data in the **Enhanced** level with Windows 10 version 1709 or later.

## Mobile device management

### Actions for non-compliance

You can now configure a time-ordered sequence of actions that are applied to devices that fall out of compliance. For example, you can notify users of non-compliant devices via e-mail or mark those devices non-compliant.

### Windows 10 ARM64 device support

Hybrid mobile device management (MDM) scenarios will be supported on ARM64 devices running Windows 10 when these devices are available.

### Improved VPN Profile Experience in Configuration Manager Console

With this release, we've updated the VPN profile wizard and properties pages to display settings appropriate for the selected platform:

- Each platform has its own workflow, meaning that new VPN profiles contain only the setting supported by the platform.
- The **Supported Platforms** page now appears after the **General** page. You now choose the platform before setting property values.
- When the platform is set to **Android**, **Android for Work**, or **Windows Phone 8.1**, the **Supported platforms** page is not needed and is not displayed.
- The Configuration Manager client-based workflow has been combined with the hybrid mobile device (MDM) client-based Windows 10 workflows; they support the same settings.
- Each platform workflow includes just the settings appropriate for that workflow. For example, the Android workflow contains settings appropriate for Android; settings appropriate for iOS or Windows 10 Mobile no longer appear in the Android workflow.
- The Automatic VPN page is obsolete and has been removed.

These changes apply to new VPN profiles.

To minimize compatibility risk, existing VPN profiles are unchanged. When you edit an existing profile, the settings appear as they did when the profile was created.

For more information, see [VPN Profiles on mobile devices](../../../protect/deploy-use/vpn-profiles).

### Limited support for Cryptography: Next Generation (CNG) certificates

Configuration Manager has limited support for Cryptography: Next Generation (CNG) certificates. Configuration Manager clients can use PKI client authentication certificate with private key in CNG Key Storage Provider (KSP). With KSP support, Configuration Manager clients support hardware-based private key, such as TPM KSP for PKI client authentication certificates.

For more information, see [CNG certificates overview](../network/cng-certificates-overview).

## Protect devices

### Create and deploy Exploit Guard policies

You can [create and deploy policies](../../../protect/deploy-use/create-deploy-exploit-guard-policy) that manage all four components of Windows Defender Exploit Guard, including attack surface reduction, controlled folder access, exploit protection, and network protection.

### Create and deploy Windows Defender Application Guard policy

You can [create and deploy Windows Defender Application Guard policies](../../../protect/deploy-use/create-deploy-application-guard-policy) by using the Configuration Manager endpoint protection.

### Device Guard policy changes

The following three changes have been made in relation to Device Guard policies:

- Device Guard policies have been renamed to Windows Defender Application Control policies. So, for example, the **Create Device Guard policy wizard** is now named **Create Windows Defender Application Control policy wizard**.
- Devices using the Fall Creators Update for Windows version 1709 don't require a restart to apply the Windows Defender Application Control policies. Restarting is still the default, but you can [turn off restarts](../../../protect/deploy-use/use-device-guard-with-configuration-manager).
- You can [set devices to automatically run software](../../../protect/deploy-use/use-device-guard-with-configuration-manager) trusted by the Intelligent Security Graph.