---
layout: Conceptual
title: Support for Windows 11 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11
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
description: Learn about the Windows 11 versions that are supported as clients with Configuration Manager.
ms.date: 2026-09-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 4c8027e2-be81-d12f-3496-c0fc9f52198a
document_version_independent_id: 5adc2117-c5be-70af-7c03-3cb5d29996ed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/support-for-windows-11.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/support-for-windows-11
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/support-for-windows-11.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3dee562d-31ba-0894-dc08-e8940a4b8dbc
---

# Support for Windows 11 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Learn about the Windows 11 versions that Configuration Manager supports as a client.

For more information about support for the Windows Assessment and Deployment Kit (ADK) for Windows 11, see [Support for the Windows ADK](support-for-windows-adk).

Note

You can continue to use Microsoft Endpoint Manager to manage devices running Windows 11 the same as with Windows 10. If another article doesn't explicitly reference Windows 11, assume that feature support for Windows 10 also includes Windows 11. This article lists some known issues.

## Windows 11 versions

Configuration Manager attempts to provide support as a client for each new Windows 11 version soon after it becomes available. Because the products have separate development and release schedules, the support that Configuration Manager provides depends on when each becomes available.

A Configuration Manager version drops from the matrix after [support for that version](../../servers/manage/current-branch-versions-supported) ends. Similarly, Configuration Manager doesn't support Windows 11 versions when their support lifecycle ends.

- The latest version of Configuration Manager current branch receives both security and critical updates, which can include fixes for Windows 11-specific features. When Microsoft releases a new version of Configuration Manager current branch, prior versions only receive security updates. For more information, see [Support for Configuration Manager current branch versions](../../servers/manage/current-branch-versions-supported).

    Note

    The best way to stay current with Windows 11 is to stay current with Configuration Manager. For more information, see [Configuration Manager and Windows as a Service](../../understand/configuration-manager-and-windows-as-service).
- This information supplements [Supported operating systems for clients and devices](supported-operating-systems-for-clients-and-devices).

The following table lists the versions of Windows 11 that you can use as a client with different versions of Configuration Manager.

| Windows 11 version | ConfigMgr 2509 | ConfigMgr 2603 | ConfigMgr 2609 |
| --- | --- | --- | --- |
| **25H2**(10.0.26200) | ✅ | ✅ | ✅ |
| **24H2**(10.0.26100) | ✅ | ✅ | ✅ |
| **23H2**(10.0.22631) | ✅ | ✅ | ✅ |

For more information on Windows lifecycle, see the [Windows lifecycle fact sheet](/en-us/lifecycle/faq/windows) and [Windows release information](/en-us/windows/release-health/windows11-release-information).

| Key |
| --- |
| ✅ = **Supported** |
| ❌ = **Not supported** |

## Support notes

- Support for Windows 11 versions includes the following editions: Enterprise, Pro, Education, Pro Education, and Pro for Workstation.
- Windows 11 reports the **Operating System** property as `Microsoft Windows NT Workstation 10.0`, which is identical to Windows 10. To distinguish devices running Windows 11, use the **Operating System Build** device property for build number `10.0.22000` or later.
- OS deployment images and upgrade packages for Windows 11 show the image name as Windows 10. For more information, see [Using deployment tools with Windows 11 images](/en-us/windows-hardware/manufacture/desktop/using-deployment-tools-with-windows-11).

- The last supported version of 32-bit WinPE is available in the **WinPE add-on for Windows 10, version 2004** (10.1.19041). Versions of the WinPE add-on for the ADK after the **ADK for Windows 10, version 2004** (10.1.19041) no longer support 32-bit versions of Windows PE (WinPE). For more information, see [Download and install the Windows ADK](/en-us/windows-hardware/get-started/adk-install).

    Configuration Manager supports the use of older versions of Windows PE as boot images, but you can't customize them in the Configuration Manager console. For more information, see [Customize boot images with Configuration Manager](../../../osd/get-started/customize-boot-images).

## Windows 11 on ARM64

Configuration Manager version 2107 with the [update rollup](../../../hotfix/2107/11121541) supports the client on Windows 11 ARM64 devices.

The **All Windows 11 (ARM64)** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists.

Starting in version 2403 OS deployment is supported for **All Windows 11 (ARM64)**, you can deploy a task sequence with a feature update to a Windows 11 on ARM64 device. For more information, see [Upgrade Windows to the latest version](../../../osd/deploy-use/upgrade-windows-to-the-latest-version).

## Support for Windows Insider

You can [update and service Windows Insider](../../../sum/get-started/configure-classifications-and-products#bkmk_WIfB) builds. This ability is provided as a convenience to our customers. While this functionality should work, its support is best effort. Configuration Manager might not issue a hotfix for this functionality if it doesn't work.

To provide feedback on Windows Insider, use the Windows [Feedback Hub](/en-us/windows-insider/business/feedback).

## Offline servicing

Due to changes in how Windows 11 updates are delivered through UUP patches, Offline Servicing of Windows 11 images and update packages using Configuration Manager is no longer supported. The recommended method to keep Windows 11 deployments up-to-date is to acquire the latest patched Windows 11 ISO from [Microsoft 365 admin center](https://admin.microsoft.com/). Once the updated Windows 11 ISO is obtained:

- Import the **install.wim** image from the ISO into the site for **Operating System Images** packages used in bare metal/refresh task sequences.
- Import the whole contents of the ISO into the site for **Operating System Upgrade Packages** used in-place upgrade task sequences.

## Known issues

### Windows servicing dashboard

The **Windows Servicing** dashboard currently includes Windows 11 devices with the latest version of Windows 10. It doesn't yet distinguish a version for Windows 11. For more information on this dashboard, see [Manage Windows as a service using Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service).

### Software Center notifications don't display during quiet period

By default, Windows 11 enables **focus assist** for the first hour after a user signs on for the first time. For more information, see [Reaching the Desktop and the Quiet Period](/en-us/windows-hardware/customize/desktop/customize-oobe-in-windows-11#reaching-the-desktop-and-the-quiet-period).

Software Center notifications are currently suppressed during this time. For more information, see [Turn Focus assist on or off in Windows](https://support.microsoft.com/windows/turn-focus-assist-on-or-off-in-windows-5492a638-b5a3-1ee0-0c4f-5ae044450e09#ID0EBD=Windows_11).

### Pre-provisioning BitLocker during task sequence doesn't own TPM

Applies to: *Windows ADK for Windows 11 (version 10.1.22000)*

When you use a Windows 11-based boot image with an OS deployment task sequence that includes the [Pre-provision BitLocker](../../../osd/understand/task-sequence-steps#BKMK_PreProvisionBitLocker) step, the step might fail. You'll see errors similar to the following strings in the smsts.log:

```log
'TakeOwnership' failed (2147942402)
pTpm->TakeOwnership(sOwnerAuth), HRESULT=80070002
Failed to take ownership of TPM. Ensure that Active Directory permissions are properly configured
The system cannot find the file specified. (Error: 80070002; Source: Windows)
Process completed with exit code 2147942402
Failed to run the action: Pre-provision BitLocker. Error -2147024894
```

To work around this issue, add a **Run Command Line** step to the task sequence before the **Pre-provision BitLocker** step. Run the following command:

`reg.exe add HKLM\SOFTWARE\Policies\Microsoft\TPM /v OSManagedAuthLevel /t REG_DWORD /d 2 /f`

For more information on this registry key, see [Change the TPM owner password](/en-us/windows/security/information-protection/tpm/change-the-tpm-owner-password). This work around is only needed for ADK releases 10.1.22000. Later versions aren't affected.

### Configuration Manager console with Windows Hello for Business authentication

*Applies to: Microsoft Entra joined devices*

If you configure the [authentication level](../hierarchy/plan-for-the-sms-provider#authentication) for the site to require **Windows Hello for Business authentication**, the Configuration Manager console on a Windows 11 device can't connect to the site. The adminui.log file on the devices shows the following errors:

```log
Description = "Current thread is not authenticated with the minimal allowed level.";
ErrorCode = 2185761792;
```

Use one of the following options to work around this issue:

- Update the device to Windows 11 OS build **22000.282**. For more information, see [October 21, 2021—KB5006746 (OS Build 22000.282) Preview](https://support.microsoft.com/topic/october-21-2021-kb5006746-os-build-22000-282-preview-03190705-0960-4ba4-9ee8-af40bef057d3).
- Install the console on a device running another version of Windows.
- Add users to the authentication exclusion list. For more information, see [Configure SMS Provider authentication](../security/configure-security#sms-provider-authentication).