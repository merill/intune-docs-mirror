---
layout: Conceptual
title: Use Windows Holographic devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/windows-holographic
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Use Microsoft Intune to manage and complete different tasks on devices running Windows Holographic for Business and HoloLens. You can configure the Company Portal app, create a compliance policy, customize OMA-URI settings, deploy apps, categorize devices in groups, create profiles, restrict devices, enable software updates, set terms and conditions, configure VPN and Wi-Fi settings, and use Hello for Business.
ms.date: 2025-03-17T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 0ae34da0-5858-0681-37a2-1c74fbdfe711
document_version_independent_id: 0ae34da0-5858-0681-37a2-1c74fbdfe711
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/windows-holographic.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/windows-holographic
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/windows-holographic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 9674171c-3b42-5610-016b-37126f38d414
---

# Use Windows Holographic devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune includes many features to help manage devices that run Windows Holographic for Business, like the [Microsoft HoloLens](/en-us/hololens/). Using Intune, you can confirm that devices are compliant with your organization's rules, and you can customize the device by adding a VPN or WiFi profile. Another key feature is to use the device as a Kiosk, and run a specific app, or a specific set of apps.

The tasks in this article help you manage, customize, and secure your devices running Windows Holographic for Business, including software updates and using Windows Hello for Business.

To use Windows Holographic devices with Intune, create an [Edition Upgrade](../device-configuration/templates/configure-edition-upgrade-windows) profile. This upgrade profile upgrades the devices from Windows Holographic to Windows Holographic for Business. For the Microsoft HoloLens, you can buy the Commercial Suite to get the required license for the upgrade. For more information, go to [Upgrade devices running Windows Holographic to Windows Holographic for Business](../device-configuration/templates/ref-holographic-upgrade-settings).

This article describes the different features and services you can use to manage devices running Windows Holographic for Business.

## Microsoft Entra ID

Microsoft Entra ID helps manage and control your devices running Windows Holographic for Business. When you use Intune and Microsoft Entra ID, you can:

- **[Join devices to Microsoft Entra ID](/en-us/entra/identity/devices/device-join-plan)**: In Microsoft Entra ID, you can add your work-owned Windows devices, including devices running Windows Holographic for Business. This feature allows Microsoft Entra ID to control the device. It helps confirm that users are accessing the company resources from devices that meet your security and compliance standards.

    For information, go to [Device identity in Microsoft Entra ID](/en-us/entra/identity/devices/overview).
- **[Bulk enrollment for Windows devices](../device-enrollment/windows/create-bulk-package)**: You can join large numbers of new Windows devices to Microsoft Entra ID and Intune. This feature is called bulk enrollment, and uses provisioning packages. These packages join the devices running Windows Holographic for Business to your Microsoft Entra tenant, and enrolls them in Intune.

## Company Portal app

**[Configure the Company Portal app](../app-management/configuration/configure-company-portal)**.

Intune provides the Company Portal app for users to access company data, enroll devices, install apps, contact their IT department, and more. You can customize the Company Portal app for your devices running Windows Holographic for Business.

In the Company Portal app, end users can run the following actions:

- [Remove a device from Intune](../user-help/unenrollment/unenroll-windows) using the Settings app or the Company Portal app
- [Rename a device](../user-help/device-actions/update-device-name-company-portal-app)
- [Install apps](../user-help/apps/install-apps-windows) on a device
- [Sync devices manually](../user-help/device-actions/sync-device-windows) from the Settings app or the Company Portal app

## Compliance policy

**[Create a device compliance policy](../device-security/compliance/ref-windows-settings)**.

Compliance policies are rules and settings that devices must meet to be compliant. Use these policies with Conditional Access to block access to company resources for devices that are noncompliant. In Intune, create compliance policies to allow or block access for devices running Windows Holographic for Business. For example, you can create a policy that requires BitLocker.

For more information, go to **[Get started with compliance policies](../device-security/compliance/overview)**.

## Deploy and manage apps

**[Add apps to Intune](../app-management/deployment/)**.

Using Intune, you can add apps to your devices running Windows Holographic for Business. There are many ways to deploy apps, including:

- [Add Microsoft Store apps](../app-management/deployment/add-microsoft-store-legacy)
- [Add line-of-business (LOB) you create](../app-management/deployment/add-lob-windows)
- [Assign apps to groups](../app-management/deployment/assign-groups)

Microsoft Intune can deploy Universal Windows Apps (UWP) to Microsoft HoloLens devices running Windows Holographic for Business. You can directly upload and deploy your app packages using the Intune admin center. For more information, go to:

- To deploy Line-of-Business (LOB) apps using the Intune admin center, go to [How to add Windows line-of-business apps to Microsoft Intune](../app-management/deployment/add-lob-windows).

    Note

    Intune allows a maximum package size to 8 GB. This package size is only available for the LOB apps uploaded to Intune.
- To learn about app management with Microsoft Intune, go to [What is app management in Microsoft Intune](../app-management/overview).
- To learn more about developing apps for Microsoft HoloLens, go to [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps).

## Device actions

Intune has some built-in actions that allow IT admins to do different tasks locally on the device, or remotely using the Intune admin center. Users can also issue a remote command from the Intune Company Portal app to personally owned devices that are enrolled in Intune.

When you manage devices running Windows Holographic for Business, the following remote actions can be used:

- **[Wipe](../device-management/actions/wipe)**: The **Wipe** action removes the device from Intune, and restores the device back to its factory default settings. Use this action before giving the device to a new user, or when the device is lost or stolen.
- **[Retire](../device-management/actions/retire)**: The **Retire** action removes the device from Intune. It also removes managed app data, settings, and email profiles assigned by Intune. The user's personal data stays on the device.
- **[Sync devices to get the latest policies and actions](../device-management/actions/sync)**: The **Sync** action forces the device to immediately check in with Intune. When a device checks in, the device receives any pending actions or policies that are assigned. This feature helps you validate and troubleshoot policies you assigned, without waiting for the next scheduled check-in.

For information about managing devices using the Intune admin center, go to [What is Microsoft Intune device management?](../device-management/actions/).

## Device categories and groups

**[Categorize devices into groups](../device-management/create-device-categories)**.

Using Intune, you can create device categories to automatically add devices to groups based on categories that you create, like Sales, Accounting, and Human Resources. The idea is to make it easier to manage your devices running Windows Holographic for Business.

## Device configuration profiles

**[Get started with configuration profiles](../device-configuration/overview) and [profile overview](../device-configuration/create-device-profile)**.

Intune includes settings and features that you can enable or disable on different devices within your organization. These settings and features are managed using configuration profiles. For example, you can create a profile that uses Microsoft Defender Smart Screen on your devices running Windows Holographic for Business.

In your profiles, you can use OMA-URI to customize some settings, create device restrictions, and configure a virtual private network (VPN) and Wi-Fi.

### [Custom device settings](../device-configuration/templates/ref-custom-settings-windows-holographic)

To configure OMA-URI (Open Mobile Alliance Uniform Resource Identifier) settings, you can create a custom profile in Intune. Use the OMA-URI settings to control different features on your Windows Holographic for Business devices. Typically, custom profiles are used to configure settings that aren't built-in to Intune.

The [HoloLens 2 devices example](../device-configuration/templates/configure-wdac-hololens) uses the [Windows Defender Application Control (WDAC) CSP](/en-us/windows/client-management/mdm/applicationcontrol-csp) to allow or block apps from opening on HoloLens 2 devices.

### [Configure kiosk mode](../device-configuration/templates/ref-kiosk-settings-windows-holographic)

Using the shared or guest PC features available in Intune, you can configure Windows Holographic for Business devices to run as a kiosk. These devices can run one app (single-app kiosk mode), or run many apps (multi-app kiosk mode).

### [Device restrictions](../device-configuration/templates/ref-device-restrictions-windows-holographic)

Device restrictions let you control different settings and features on your devices. For example, you can require a password, install apps from [Microsoft Store](https://apps.microsoft.com/home?icid=CNavAppsWindowsApps), and enable Bluetooth. These restrictions are created in an Intune configuration profile. This profile can be applied to multiple devices running Windows Holographic for Business.

### [Configure VPN](../device-configuration/templates/configure-vpn)

Virtual private networks (VPNs) give your users secure remote access to your organization network. In Intune, you can create a VPN profile that includes specific settings for your devices running Windows Holographic for Business. For example, you can create a VPN profile so all Windows Holographic for Business devices use Citrix VPN as the connection type.

Note

When assigning a VPN policy to Windows Holographic for Business devices, assign the profile to the device scope. Currently, Windows Holographic only supports the device scope. When the VPN profile is installed in the device context, it applies to all users on the device. If a user profile is deployed, it's treated as a device profile.

### [Configure Wi-Fi](../device-configuration/templates/configure-wifi)

You can also create a Wi-Fi profile in Intune to assign wireless network settings to your Windows Holographic for Business devices. When you assign a Wi-Fi profile, your end users get corporate network access, without any network configuration. For example, you can create a Wi-Fi network dedicated to only your Windows Holographic for Business devices.

## Shared multi-user devices

Devices that run Windows Holographic for Business, like the Microsoft HoloLens, can have multiple users. Intune includes settings to control different features on these shared devices, like power management, using the local storage, and account management. The configuration profiles can also be applied to devices with different operating systems.

For more information, go to [Shared devices](../device-configuration/templates/ref-shared-device-settings-windows-holographic).

## Software updates

**[Manage software updates](../device-updates/windows/)**.

Intune has different feature that focus on updating Windows client devices. These options include that determine how updates are installed. For example, you can create a maintenance window to install updates, or choose to restart after updates are installed. Updates can be applied to multiple devices running Windows Holographic for Business.

## Terms and conditions

**[Set your company's terms and conditions for user access](../device-enrollment/create-terms-and-conditions)**.

Before users enroll devices and access your company apps, including email, you can require that users accept your company's terms and conditions. In Intune, define how the terms and conditions are shown in the Company Portal app, and also assign these terms and conditions to devices running Windows Holographic for Business.

## Windows Hello for Business

**[Use Windows Hello for Business](../device-security/identity-protection/configure-tenant-wide-policy)**.

Hello for Business is an alternative sign-in method that uses a Microsoft Entra account to replace a password, smart card, or a virtual smart card. With Hello for Business, your Windows Holographic for Business devices can sign in with a PIN with a minimum length set by you.