---
layout: Conceptual
title: Use Microsoft Intune policies to manage macOS software updates - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/apple/deprecated-mdm-policies-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Use Microsoft Intune to manage system updates for supervised macOS devices.
ms.date: 2025-09-24T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: ee9a79cb-f053-b325-20d9-0c247cddc517
document_version_independent_id: ee9a79cb-f053-b325-20d9-0c247cddc517
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/apple/deprecated-mdm-policies-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/apple/deprecated-mdm-policies-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/apple/deprecated-mdm-policies-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0c49a641-d721-451d-2dc6-ad16277765c7
---

# Use Microsoft Intune policies to manage macOS software updates - Microsoft Intune | Microsoft Learn

Important

Apple has deprecated MDM‑based software update workloads. To align with this change, Microsoft Intune will soon end support for MDM‑based Apple software update policies. Microsoft recommends using declarative device management (DDM) to manage and install Apple software updates. For more information about this transition, see the [Intune Customer Success blog: Move to declarative device management for Apple software updates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-move-to-declarative-device-management-for-apple-software-updates/4432177).

You can use Microsoft Intune to manage software updates for macOS devices that enrolled as [supervised devices](../../device-enrollment/apple/methods-macos#user-approved-enrollment). With these MDM-based policies, you can:

- Remotely manage how downloads, installations, and notifications should occur when the following types of updates are available:

    - Critical update
    - Firmware update
    - Configuration file update
    - All other updates (OS, built-in apps)
- Create a schedule that determines when the update installs. Schedules can be simple, like installing updates the next time that the device checks in. Or, you can create day-time ranges when updates can install or when they're blocked from installing.

By default, devices check in with [Intune about every 8 hours](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals). If an update is available through an update policy, the device downloads the update. The device then installs the update upon next check-in within your schedule configuration.

This feature applies to:

- macOS 12 - macOS 15 (supervised)

## Configure the policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

    Tip

    For more information on managing software updates and the update experience on devices, see [Manage software updates for Apple devices - Apple Support](https://support.apple.com/guide/deployment/depafd2fad80/1/web/1.0) at Apple's Platform Deployment site.
2. Select **Devices** &gt; **Update policies for macOS** &gt; **Create profile**.
3. On the **Basics** tab, specify a name for this policy, specify a description (optional), and then select **Next**.
4. On the **Update policy settings** tab, configure the following options:

    ![Screen capture of the Update policy settings page.](media/deprecated-mdm-policies-macos/macos-update-policy-settings.png)

    1. For *Critical*, *Firmware*, *Configuration file*, and *All other updates (OS, built-in apps)*, the following installation actions can be configured:

        - **Download and install**: Download or install the update, depending on the current state.
        - **Download only**: Download the software update without installing it.
        - **Install immediately**: Download the software update and trigger the restart countdown notification. This action is recommended for userless devices.
        - **Notify only**: Download the software update and notify the user through System Settings.
        - **Install later**: Download the software update and install it later. This action isn't available for major OS upgrades.

            When you configure *Install later* for \*All other updates (OS, built-in-apps), the following settings are also available:

            - **Max User Deferrals**: When the *All other updates* update type is configured to *Install later*, this setting allows you to specify the maximum number of times a user can postpone a minor OS update before it's installed. The system prompts the user once a day. Available for devices running macOS 12 and later.
            - **Priority**: When the *All other updates* update type is configured to *Install later*, specify *Low* or *High* values for the scheduling priority for downloading & preparing minor OS updates. Available for devices running macOS 12.3 and later.
        - **Not configured**: No action taken on the software update.

        Note

        Devices with Apple Silicon require an MDM-issued bootstrap token to authenticate automated, non-interactive updates and upgrades.
    2. **Schedule type**: Configure the schedule for this policy:

        - **Update at next check-in**: The update installs on the device the next time it checks in with Intune. This option is the simplest and has no extra configurations.
        - **Update during scheduled time**: You configure one or more windows of time. During these windows, the update installs upon check-in.
        - **Update outside of scheduled time**: You configure one or more windows of time. During these windows, updates don't install upon check-in.
    3. **Weekly schedule**: If you choose a schedule type other than *update at next check-in*, configure the following options:

        ![Screen capture of the Update policy schedule settings.](media/deprecated-mdm-policies-macos/update-policy-schedule-settings.png)

        - **Time zone**: Choose a time zone.
        - **Time window**: Define one or more blocks of time that restrict when the updates install. The effect of the following options depends on the Schedule type you selected. With a start day and end day, overnight blocks are supported. Options include:
        - **Start day**: Choose the day on which the schedule window starts.
        - **Start time**: Choose the time day when the schedule window begins. For example, you select 5 AM and have a Schedule type of *Update during scheduled time*. In this scenario, 5 AM is the time that updates can begin to install. If you chose a Schedule type of *Update outside of a scheduled time*, 5 AM is the start of a period of time that updates can't install.
        - **End day**: Choose the day on which the schedule window ends.
        - **End time**: Choose the time of day when the schedule window stops. For example, you select 1 AM and have a Schedule type of *Update during scheduled time*. In this scenario, 1 AM is the time when updates can no longer install. If you chose a Schedule type of *Update outside of a scheduled time*, 1 AM is the start of a period of time that updates can install.

    If you don't configure times to start or end, the configuration results in no restriction and updates can be installed at any time.

    Tip

    You can deploy a settings catalog policy to hide an update from device users for a specified period of time on your supervised macOS devices. For more information, see the following section Delay visibility of updates.
5. After configuring *Update policy settings*, select **Next**.
6. On the **Scope tags** tab, select **+ Select scope tags** to open the *Select tags* pane if you want to apply them to the update policy.

    - On the **Select tags** pane, choose one or more tags, and then **Select** to add them to the policy and return to the *Scope tags* pane.
    - When ready, select **Next** to continue to *Assignments*.
7. On the **Assignments** tab, choose **+ Select groups to include** and then assign the update policy to one or more groups. Use **+ Select groups to exclude** to fine-tune the assignment. When ready, select **Next** to continue.

    The devices used by the users targeted by the policy are evaluated for update compliance. This policy also supports userless devices.
8. On the **Review + create** tab, review the settings, and then select **Create** when ready to save your macOS update policy. Your new policy is displayed in the list of update policies for macOS.

Note

Apple Mobile Device Management (MDM) doesn't allow you to force a device to install updates by a certain time or date. You can't use Intune software update policies to downgrade the OS version on a device.

## Delay visibility of updates

When you use update policies for macOS, you might want to hide updates from users of supervised macOS devices for a specified time period. For this task, use a settings catalog policy for macOS devices that configures update restriction periods.

A restriction period gives you time to test an update before users can install it. After the restriction period ends, the update becomes visible to users, and they can choose to install it if your update policies don't install it first.

If you use device restrictions to hide an update, review your software update policies to ensure they don't schedule the installation of that update before the restriction period ends. Software update policies install updates per their schedule regardless of the update being hidden or visible to the device user.

The settings that can restrict visibility of updates on macOS devices are in the [settings catalog](../../device-configuration/settings-catalog/) &gt; **Restrictions** category. A few examples of settings you can use to defer an update include:

- Enforced Software Update Delay
- Enforced Software Update Major OS Deferred Install Delay
- Enforced Software Update Non OS Deferred Install Delay

You can also find related settings under the **System Updates** &gt; **Software Update** category to manage how users manually interact with updates through their system UI. However, updates from a targeted update policy override these settings catalog policy settings.

## Edit a policy

You can edit an existing policy, including changing the restricted times:

1. Select **Devices** &gt; **Update policies for macOS**. Select the policy you want to edit.
2. While viewing the policies **Properties**, select **Edit** for the policy page you want to modify.

    ![Screen capture of the policy edit page.](media/deprecated-mdm-policies-macos/edit-a-macos-update-policy.png)
3. After introducing a change, select **Review + save** &gt; **Save** to save your edits.

Note

If the **Start time** and **End time** are both set to 12 AM, Intune doesn't check for restrictions on when to install updates. Any configurations you have for **Select times to prevent update installations** are ignored, and updates can install at any time.

## Configure more macOS software update settings using the Settings Catalog

The *Restrictions* category contains the following settings that can be used to delay visibility of macOS software updates on devices (**Devices** &gt; **By platform** &gt; **macOS** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Settings catalog** &gt; **Restrictions**):

- *Enforced Software Update Delay*: Sets how many days to delay a software update on the device. With this restriction in place, the user doesn't see a software update until the specified number of days after the software update release date. This value is used by *Force Delayed App Software Updates* and *Force Delayed Software Updates*.
- *Force Delayed App Software Updates*: If true, delays user visibility of non-OS Software Updates for built-in software like Safari, XProtect, and Gatekeeper. Requires a supervised device. The delay is 30 days unless *Enforced Software Update Delay* is set to another value.
- *Enforced Software Update Non OS Deferred Install Delay*: This restriction allows the admin to set how many days to delay an app software update on the device. When this restriction is in place, the user sees a non-OS software update only after the specified delay after the release of the software. This value controls the delay for Force Delayed App Software Updates.
- *Force Delayed Major Software Updates*: If set to true, delays user visibility of major upgrades to OS Software.
- *Enforced Software Update Major OS Deferred Install Delay*: This restriction allows the admin to set how many days to delay a major software upgrade on the device. Major software upgrades are new major OS releases; for example, macOS 12 Monterrey and macOS 13 Ventura. When this restriction is in place, the user sees a software upgrade only after the specified delay after the release of the software upgrade. This value controls the delay for *Force Delayed Major Software Updates*.
- *Force Delayed Software Updates*: If true, delays user visibility of software updates. In macOS, seed build updates are allowed, without delay. The delay is 30 days unless *Enforced Software Update Delay* is set to another value.
- *Enforced Software Update Minor OS Deferred Install Delay*: This restriction allows the admin to set how many days to delay a minor OS software update on the devices. Minor software updates are intermediate updates that are released between major OS upgrades; for example, macOS 13.1 and macOS 13.2. When this restriction is in place, the user sees a software update only after the specified delay after the release of the software update. This value controls the delay for *Force Delayed Software Updates*.

The Software Update category contains the following settings that can be used to configure the user experience for macOS software update options on devices (**Devices** &gt; **By platform** &gt; **macOS** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Settings catalog** &gt; **System Updates** &gt; **Software Update**):

- *Allow Pre Release Installation*: If true, prerelease software can be installed on this computer.
- *Automatic Check Enabled*: If false, deselects the "Check for updates" option and prevents the user from changing the option.
- *Automatic Download*: If false, deselects the "Download new updates when available from the App Store" option and prevents the user from changing the option.
- *Automatically Install App Updates*: If false, deselects the "Install app updates from the App Store" option and prevents the user from changing the option.
- *Automatically Install macOS Updates*: If false, restricts the "Install macOS Updates" option and prevents the user from changing the option.
- *Config Data Install*: If false, restricts the automatic installation of configuration data.
- *Critical Update Install*: If false, disables the automatic installation of critical updates and prevents the user from changing the "Install system data files and security updates" option.
- *Restrict Software Update Require Admin To Install*: If true, restrict app installations to admin users. This key has the same function as the Restrict Store Require Admin To Install setting in the App Store category.

## Monitor for update installation failures on devices

In the Microsoft Intune admin center, go to **Devices** &gt; **Monitor** &gt; **Installation status for macOS devices**.

Intune lists supervised macOS devices targeted by an update policy. The list doesn't include devices that are up-to-date and healthy because macOS devices only return information about installation failures.

For each device on the list, the Installation Status displays the error that the device returns. To view the list of potential installation status values, on the *Installation status for macOS devices* page, select **Filters** and then expand the drop-down list for *Installation Status*.