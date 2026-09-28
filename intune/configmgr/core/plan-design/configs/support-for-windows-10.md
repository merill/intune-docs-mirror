---
layout: Conceptual
title: Support for Windows 10 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10
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
description: Learn about the Windows 10 versions that are supported as clients with Configuration Manager.
ms.date: 2026-09-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ce35f51b-8368-6cfa-868c-404a3e533b67
document_version_independent_id: f4b5e0ed-226f-5811-dfa0-628bf57a0bbd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/support-for-windows-10.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/support-for-windows-10
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/support-for-windows-10.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 05cd97a3-dfbe-8258-a5a2-fbdee2e11cc2
---

# Support for Windows 10 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Learn about the Windows 10 versions that Configuration Manager supports as a client. For more information about support for later versions of Windows, see [Support for Windows 11](support-for-windows-11).

For more information about support for the Windows Assessment and Deployment Kit (ADK) for Windows 10, see [Support for the Windows ADK](support-for-windows-adk).

Tip

Windows Server builds as a client are supported the same as the associated Windows 10 version. For example, Windows Server 2016 is the same build version as Windows 10 LTSB 2016, and Windows Server version 1803 is the same build version as Windows 10, version 1803.

For more information on Windows Server as a site system, see [Supported operating systems for Configuration Manager site system servers](supported-operating-systems-for-site-system-servers).

## Windows 10 versions

Configuration Manager attempts to provide support as a client for each new Windows 10 version as soon as possible after it becomes available. Because the products have separate development and release schedules, the support that Configuration Manager provides depends on when each becomes available.

A Configuration Manager version drops from the matrix after [support for that version](../../servers/manage/current-branch-versions-supported) ends. Similarly, support for Windows 10 versions like the Enterprise 2015 LTSB or 1511 drops from the matrix when they're removed from support.

- The latest version of Configuration Manager current branch receives both security and critical updates, which can include fixes for issues with Windows 10 versions. When Microsoft releases a new version of Configuration Manager current branch, prior versions only receive security updates. For more information, see [Support for Configuration Manager current branch versions](../../servers/manage/current-branch-versions-supported).

    Note

    The best way to stay current with Windows 10 is to stay current with Configuration Manager. For more information, see [Configuration Manager and Windows as a Service](../../understand/configuration-manager-and-windows-as-service).
- This information supplements [Supported operating systems for clients and devices](supported-operating-systems-for-clients-and-devices).
- If you use the long-term servicing branch of Configuration Manager, see [Supported configurations for the long-term servicing branch](../../understand/supported-configurations-for-ltsb).

The following table lists the versions of Windows 10 that you can use as a client with different versions of Configuration Manager.

| Windows 10 version | ConfigMgr 2509 | ConfigMgr 2603 | ConfigMgr 2609 |
| --- | --- | --- | --- |
| **22H2**(10.0.19045) ^[Extended Security Updates](supported-operating-systems-for-clients-and-devices#bkmk_ESU)^ | ✅ | ✅ | ✅ |

All currently supported versions of Configuration Manager current branch support the following Windows 10 LTSB/LTSC editions:

- **Enterprise 2016 LTSB**
- **Enterprise LTSC 2019**
- **Enterprise LTSC 2021**

For more information on Windows lifecycle, see the [Windows lifecycle fact sheet](/en-us/lifecycle/faq/windows) and [Windows 10 release information](/en-us/windows/release-health/release-information).

| Key |
| --- |
| ✅ = **Supported** |
| ❌ = **Not supported** |

## Support notes

- Support for Windows 10 semi-annual channel versions includes the following editions: Enterprise, Pro, Education, Pro Education, and Pro for Workstation.
- OS deployment media shows the build number from the base version. For example, `10.0.19041`. When Windows is installed, it applies an enablement package, which updates the build number to what's in the preceding table. You can use the revision ID to distinguish the media:

    | Media version | Windows version |
    | --- | --- |
    | `10.0.19045.2130` | Windows 10, version 22H2 |
    | `10.0.19041.1288` | Windows 10, version 21H2 |

## Windows 10 on ARM64

Configuration Manager supports the client on Windows 10 ARM64 devices.

The **All Windows 10 (ARM64)** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists.

Note

If you previously selected the top-level **Windows 10** platform, this action automatically selected both **All Windows 10 (64-bit)** and **All Windows 10 (32-bit)**. If you want to add **All Windows 10 (ARM64)**, manually select it in the list.

Starting in version 2403 OS deployment is supported for **Windows 10 22H2 (ARM64)**, you can deploy a task sequence with a feature update to a Windows 10 on ARM64 device. For more information, see [Deploy a feature update with a task sequence](../changes/whats-new-in-version-2103#deploy-a-feature-update-with-a-task-sequence).

## Support for Windows Insider

You can [update and service Windows Insider](../../../sum/get-started/configure-classifications-and-products#bkmk_WIfB) builds. This ability is provided as a convenience to our customers. While this functionality should work, the support for it is best effort. Configuration Manager might not issue a hotfix for this functionality if it ceases to function.

To provide feedback on Windows Insider, use the [Feedback Hub](/en-us/windows-insider/business/feedback).

## Sysprep and Windows 10, version 20H2

If you manually customize a reference computer that runs Windows 10, version 20H2, and then use [capture media](../../../osd/deploy-use/create-capture-media), Windows Sysprep fails with the following entry in the sysprep.log: `Failed to clean the package repository database: 0x80070005.` This issue happens when you sign in to the device and create a user profile.

To work around this issue, choose one of the following options:

- Use the default image file (install.wim) from the installation media. Use the task sequence to apply configurations at run time.
- [Create a task sequence to capture an OS](../../../osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)
- Remove appx packages for the signed-in user before you use capture media. For more information, see [Sysprep fails after you remove or update Microsoft Store apps that include built-in Windows images](/en-us/troubleshoot/windows-client/deployment/sysprep-fails-remove-or-update-store-apps).
- Manually run Sysprep, and then boot to the capture media to capture the image.