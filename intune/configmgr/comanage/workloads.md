---
layout: Conceptual
title: Co-management workloads - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/workloads
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
description: Learn about the workloads that you can switch from Configuration Manager to Microsoft Intune.
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: article
ms.subservice: co-management
ms.collection: tier3
locale: en-us
document_id: 03000b95-a54a-d55c-6ea6-9202de578371
document_version_independent_id: 3982a621-fd4b-d20a-6e2a-d600597f0cf8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/workloads.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/workloads
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/workloads.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 497a8032-df41-2040-0b78-2632c034493a
---

# Co-management workloads - Configuration Manager | Microsoft Learn

You don't have to switch any of the workloads. When you're ready, you can switch them individually, several at once, or all at the same time. However, until you switch the workloads over to Intune, Configuration Manager continues to manage the workloads that you don't switch to Intune, along with all other features of Configuration Manager that co-management doesn't support.

If you switch a workload to Intune, but later change your mind, you can switch it back to Configuration Manager, although there might be an impact. For example, Windows and Office versions will remain at a later version if installed by Intune.

Co-management supports the following workloads:

- Compliance policies
- Windows Update policies
- Resource access policies
- Endpoint Protection
- Device configuration
- Office Click-to-Run apps
- Client apps

## Compliance policies

Compliance policies define the rules and settings that a device must comply with to be considered compliant by Conditional Access policies. Also use compliance policies to monitor and remediate compliance issues with devices independently of Conditional Access. You can add evaluation of custom configuration baselines as a compliance policy assessment rule. For more information, see [Include custom configuration baselines as part of compliance policy assessment](../compliance/deploy-use/create-configuration-baselines#bkmk_CAbaselines).

For more information on the Intune feature, see [Use compliance policies to set rules for devices you manage with Intune](../../device-security/compliance/overview).

## Windows Update policies

Windows Update client policies (formerly known as Windows Update for Business policies) let you configure deferral policies for Windows 10 or later feature updates or quality updates for Windows 10 or later devices.

After moving the Windows Update workload to Intune, the client settings in Configuration Manager need to be adjusted manually. Either modify existing client settings, or create a new custom client setting to disable the software update workflow. Deploy the setting to the collection of computers that are connected directly to Windows Update (which was also called Windows Update for Business).

Note

To use Windows Autopatch with these devices, this workload must be moved to Intune, and client settings for Software Updates set to 'No' in Configuration Manager. For more information, see [Prerequisites for Windows Autopatch](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites).

For more information on the Intune feature, see [Manage Windows software updates in Intune](../../device-updates/windows/).

## Resource access policies

Important

Starting in version 2203, these company resource access features of Configuration Manager and this co-management workload are no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../protect/plan-design/resource-access-deprecation-faq).

Resource access policies configure VPN, Wi-Fi, email, and certificate settings on devices.

For more information on the Intune feature, see [Deploy resource access profiles](../../device-configuration/overview).

Note

The resource access workload is also part of device configuration. These policies are managed by Intune when you switch the Device Configuration workload. Starting in version 2403, The resource access policies node is removed from console. Slider is mandated to Intune and upgrade is blocked if old policies are still available.

## Endpoint Protection

The Endpoint Protection workload includes the Defender suite of protection features:

- Microsoft Defender Antivirus
- Microsoft Defender Application Guard
- Microsoft Defender SmartScreen
- Microsoft Defender for Endpoint (formally known as Windows Defender Advanced Threat Protection)
- Windows Defender Firewall
- Windows Encryption (also known as BitLocker)
- Windows Defender Exploit Guard
- Windows Defender Application Control
- Windows Defender Security Center

For more information on the Intune feature, see [Windows 10 (and later) settings to protect devices using Intune](../../device-configuration/endpoint-security/ref-endpoint-protection-settings-windows).

Note

When you switch this workload, the Configuration Manager policies stay on the device until the Intune policies overwrite them. This behavior makes sure that the device still has protection policies during the transition.

The Endpoint Protection workload is also part of device configuration. The same behavior applies when you switch the Device Configuration workload.

When the Endpoint Protection workload resides with Intune, Windows Information Protection settings will apply from both Configuration Manager and Intune. Configuration Manager will continue to apply Windows Information Protection policy until the Device Configuration workload is moved to Intune.

The Microsoft Defender Antivirus settings that are part of the Device restrictions profile type for Intune Device configuration are not included in scope of the Endpoint protection slider. To manage Microsoft Defender Antivirus for co-managed devices with the endpoint protection slider enabled, use the new Antivirus policies in **Microsoft Intune admin center** &gt; **Endpoint security** &gt; **Antivirus**. The new policy type has new and improved options available, and support all of the same settings available in the Device restrictions profile. 

The Windows Encryption feature includes BitLocker management. For more information on the behavior of this feature with co-management, see [Deploy BitLocker management](../protect/deploy-use/bitlocker/deploy-management-agent#co-management-and-intune).

## Device configuration

The device configuration workload includes settings that you manage for devices in your organization. Switching this workload also moves the **Resource Access** and **Endpoint Protection** workloads.

You can still deploy settings from Configuration Manager to co-managed devices even though Intune is the device configuration authority. This exception might be used to configure settings that your organization requires but aren't yet available in Intune. Specify this exception on a [Configuration Manager configuration baseline](../compliance/deploy-use/create-configuration-baselines). Enable the option to **Always apply this baseline even for co-managed clients** when creating the baseline. You can change it later on the **General** tab of the properties of an existing baseline.

To use Windows Autopatch with these devices, this workload needs to be managed by Intune. For more information, see [Prerequisites for Windows Autopatch](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites).

For more information on the Intune feature, see [Create a device profile in Microsoft Intune](../../device-configuration/create-device-profile).

Note

A policy created from the settings catalog is controlled by the Device Configuration workload slider regardless of the contents of the policy.

When you switch the device configuration workload, it also includes policies for the Windows Information Protection feature. Only policies from Intune will apply once the Device Configuration workload is moved to Intune.

Note

In order to tattoo remove Endpoint protection settings, Device Configuration workload also needs to be switched.

## Office Click-to-Run apps

This workload manages Microsoft 365 Apps on co-managed devices.

- After moving the workload, the app shows up in the **Company Portal** on the device
- Office updates may take around 24 hours to show up on client unless the devices are restarted
- There's a [global condition](../apps/deploy-use/create-global-conditions) that's added by default as a requirement to new Microsoft 365 applications. When you transition this workload, co-managed clients don't meet the requirement on the application. Then they don't install Microsoft 365 deployed via Configuration Manager. The global condition is named either:

    - **Microsoft 365 apps managed by Microsoft Intune** (version 2111 or later)
    - **Are Office 365 applications managed by Intune on the device** (version 2107 and earlier)

Updates can be managed using either of the following features:

- [Use Update Channel and Target Version settings to update Microsoft 365 with Microsoft Intune settings catalog](../../device-configuration/settings-catalog/update-office)
- [Manage Microsoft 365 Apps with Configuration Manager](../sum/deploy-use/manage-office-365-proplus-updates).

Note

To use Windows Autopatch with these devices, this workload needs to be managed by Intune. For more information, see [Prerequisites for Windows Autopatch](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites).

For more information on the Intune feature, see [Add Microsoft 365 apps to Windows devices with Microsoft Intune](../../app-management/deployment/add-microsoft-365-windows).

## Client apps

Tip

This feature may appear in the list of features as **Mobile apps for co-managed devices**.

Use Intune to manage client apps and PowerShell scripts on co-managed Windows 10 or later devices. After you transition this workload, any available apps deployed from Intune are available in the Company Portal. Apps that you deploy from Configuration Manager are available in Software Center.

For more information on the Intune feature, see [What is Microsoft Intune app management?](../../app-management/overview)

Note

In Windows 10 version 1903 and later, PowerShell scripts still run on co-managed devices even if you haven't switched the **Client Apps** workload to Intune.

When you enable Microsoft Connected Cache on your Configuration Manager distribution points, they can serve Microsoft Intune Win32 apps to co-managed clients. For more information, see [Microsoft Connected Cache with Configuration Manager](../core/plan-design/hierarchy/microsoft-connected-cache#support-for-intune-win32-apps).

For example, if you wish to deploy the new Store applications (winget) via Microsoft Intune, you need to switch this workload.

## Diagram for app workloads

[![Diagram of co-management app workloads.](media/co-management-apps.svg)](media/co-management-apps.svg#lightbox)

Tip

You can configure the Company Portal to also show Configuration Manager apps. If you change this app portal experience, it changes the behaviors described in the above diagram. For more information, see [Use the Company Portal app on co-managed devices](company-portal).