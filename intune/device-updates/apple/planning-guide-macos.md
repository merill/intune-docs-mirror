---
layout: Conceptual
title: Admin guide and checklist for macOS software updates - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/apple/planning-guide-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Guidance and advice for administrators that create and manage software updates for macOS devices using Microsoft Intune. Use this article to help manage software updates on your organization-owned devices, including how to create policies, manage updates, and review update status.
ms.date: 2025-07-23T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm, ahamil, rogerso
locale: en-us
document_id: 9c25218d-07ea-5009-7d7b-e15a0a14f59d
document_version_independent_id: 9c25218d-07ea-5009-7d7b-e15a0a14f59d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/apple/planning-guide-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/apple/planning-guide-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/apple/planning-guide-macos.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 04e9e84a-8e9c-42d7-c181-85aff996091e
---

# Admin guide and checklist for macOS software updates - Microsoft Intune | Microsoft Learn

Keeping your devices current with updates is critical. Admins must do what they can to reduce risk of security events, and reduce this risk with minimal disruption to the business & users.

Intune has built-in policies that can manage software updates. For macOS devices, you can use Intune to manage device updates, configure when devices are updated, and review the device update status.

Use this article as an admin guide for your enrolled and managed macOS devices. This information can help you manage software updates on your organization-owned devices.

This article applies to:

- macOS devices enrolled in Intune

Tip

- If your devices are personally owned, then go to the [software updates admin guide for personal devices](../byod-planning-guide).
- Apple has deprecated MDM‑based software update workloads. To align with this change, Microsoft Intune will soon end support for MDM‑based Apple software update policies. Microsoft recommends using declarative device management (DDM) to manage and install Apple software updates. For more information about this transition, see the [Intune Customer Success blog: Move to declarative device management for Apple software updates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-move-to-declarative-device-management-for-apple-software-updates/4432177).

## Before you begin

To install updates faster and avoid delays, make sure the devices are:

- Powered on; not shut down but can be can a sleep state
- Plugged in
- Connected to Internet

## Manage updates with policies

✅ Do create policies that update your devices.

By default, users receive notifications and/or see the latest updates available on their devices (Settings &gt; General &gt; Software Updates). Users can choose to download and install updates whenever they want.

They can also change the update behavior using the Automatic Updates feature on the device (Settings &gt; Software Updates):

![The operating system default update settings and controls on a macOS Apple device.](media/planning-guide-macos/default-update-settings-macos-device.png)

When users install their own updates (instead of admins managing the updates), it can disrupt user productivity and business tasks. For example:

- Users can apply updates that your organization hasn't approved. This situation can cause issues with application compatibility, or changes to the operating system or user experience that disrupt device use.
- Users can avoid applying updates that are required for security or app compatibility reasons. This delay can leave the devices at risk and/or prevent them from being able to function.
- Users can disable checking for new updates entirely.

Because of these potential issues, Microsoft recommends that you evaluate your use case scenarios and deploy policies to manage the update experience to minimize risk and disruption to your business.

## Admin steps for organization owned devices

To update macOS devices owned by your organization, Microsoft recommends the following features. You can also use these features as a starting point for your own update strategy.

### ✅ Use DDM-managed software updates on macOS 14 and newer

On macOS 14 and newer devices, use Apple's declarative device management (DDM) to install a specific update by an enforced deadline.

DDM is the modern way to manage settings. The independent nature of DDM provides an improved user experience, as the device handles the entire software update lifecycle. It prompts users that an update is available and also downloads the update, prepares the device for the installation, & installs the update.

Don't use the MDM-based software update policy settings on these devices, as Apple deprecated the MDM policies.

The DDM settings are configurable in the [Intune settings catalog](../../device-configuration/settings-catalog/). For more information, go to [Managed software updates with the settings catalog](./).

### ✅ Use MDM on macOS 13 and older

On macOS versions 13 and older, you can use Apple's MDM settings built-in to Intune. For these devices, you create two policies that work together to manage the update experience. The first policy manages when updates are installed, and the second policy manages how updates are installed.

#### Step 1 - Use a software update policy to manage when updates are installed

In a software update policy, you can manage when critical updates and firmware updates are installed. You can also manage how many times the user can defer an update before it's force installed. Depending on the settings you enter, users aren't prompted and don't need to be using the device when the updates are installed.

For most organizations, Microsoft recommends you configure the settings available in a [software update policy](deprecated-mdm-policies-macos).

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Apple updates &gt; macOS update policies**.
2. Configure the following settings:

    - **Update policy behavior settings**

        - **Critical updates**: Install later
        - **Firmware updates**: Install later
        - **Configuration file updates**: Install later
        - **All other updates (OS, built-in apps)**: Install later
            - **Maximum user deferrals**: 5
            - **Priority**: High

        Note

        - On recent macOS builds, almost all updates show as **Configuration data files** or **All other updates**. The **All other updates** settings are mostly legacy updates for older builds of macOS.
        - The time specified in these settings is used by the Intune service. The time isn't the local device time. Be aware of time differences when you configure a maintenance window, especially for a global environment.
    - **Update policy schedule settings**

        - **Schedule type**: Update at next check-in

        You can change the values to your preferred scheduled times. Some of the values might only affect minor updates, and not major updates.

For the specific steps, and more information on these settings & their values, go to [Manage macOS software update policies in Intune](deprecated-mdm-policies-macos).

##### End user experience

With these settings, this policy locks these settings so users can't change them. The policy also:

1. Checks for updates each time the device checks in with the Intune service. If there are updates available, then they're automatically downloaded.
2. The device finds a time period when the device isn't being used.

    - If the device isn't being used, then the policy tries to automatically install the update.
    - If the device is being used, then end users can choose to install the update, or defer the installation up to five times. Be sure to encourage your end users to install updates when they're available.

    The following images show the prompts that end users can see when updates are available:

    ![The sample notification prompt for a required update on a macOS Apple device.](media/planning-guide-macos/required-managed-update-sample-notification-macos.png)

    ![The sample notification that an update is available on a macOS Apple device.](media/planning-guide-macos/updates-available-sample-notification-macos.png)
3. If end users use all the deferrals, then the update is force installed. For a forced installation, a restart doesn't prompt the end user, and could result in data loss.

#### Step 2 - Use a settings catalog policy to manage how updates are installed

The [Intune settings catalog](../../device-configuration/settings-catalog/) includes settings to help manage software updates. In this step, you create a policy that:

- Configures the device to automatically install updates when they're available, including app updates.
- Prevents end users from disabling update checks.
- Configures the device to check for updates and prompt users regularly.

This settings catalog policy works with Step 1 - Use a software update policy to manage when updates are installed (in this article). It makes sure the devices are checking for updates and prompting users to install them. End users still need to take action to finish the installation.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Manage devices &gt; Configuration &gt; Settings catalog &gt; Software Update**.
2. Configure the following settings:

    - **Allow Pre Release Installation**: False
    - **Automatic Download**: True
    - **Automatically Install App Updates**: True
    - **Critical Update Install**: True
    - **Restrict Software Update Require Admin To Install**: False
    - **Config Data Install**: True
    - **Automatically Install MacOS Updates**: True
    - **Automatic Check Enabled**: True

For more information on the settings catalog, including how to create a settings catalog policy, go to [Use the settings catalog to configure settings](../../device-configuration/settings-catalog/).

##### End user experience

This policy locks these settings so users can't change them. On the device, the software update settings are greyed out:

![The software update settings are greyed out after the Intune settings catalog update policy applies to a macOS Apple device.](media/planning-guide-macos/update-settings-with-settings-catalog-policy-macos.png)

### ✅ Consider using the Nudge community tool

This tool is optional, and can help you **manage the end user experience**.

A popular tool within the Microsoft macOS admin community is Nudge. [Nudge is an open source community tool](https://github.com/macadmins/nudge) that encourages end users to install macOS updates. It provides a rich configuration experience for admins.

When Nudge is configured and deployed, end users see the following sample message when their device is ready to be updated. End users can also choose to update the device or defer the update:

[![A sample Nudge community tool message when a software update is available a macOS Apple device.](media/planning-guide-macos/nudge-sample-notification-message-macos.png)](media/planning-guide-macos/nudge-sample-notification-message-macos.png#lightbox)

There's also a [sample script and Intune configuration policy](https://github.com/microsoft/shell-intune-samples/tree/master/macOS/Apps/Nudge) for Nudge in the Microsoft shell script repository. This script includes everything you need to get started with Nudge. Make sure you update the `.mobileconfig` file with your values.

### ✅ Use built-in reporting for update status

After the update policies are deployed, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), you can use the reporting feature to check the status of the updates.

For each device, you can see its current state of updates (Devices &gt; macOS &gt; Update policies for macOS):

[![Use the built-in reporting to check the update status of a macOS Apple device in the Microsoft Intune admin center.](media/planning-guide-macos/device-update-category-status.png)](media/planning-guide-macos/device-update-category-status.png#lightbox)