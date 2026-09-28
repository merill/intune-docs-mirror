---
layout: Conceptual
title: See device configuration policies with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- msec-ai-copilot
ms.subservice: configuration
description: See and manage the device configuration policy details in Microsoft Intune. Look at a graphical chart of the number of devices assigned to a policy, and see which devices have policies assigned or deployed. Can also troubleshoot policies that have conflict settings.
ms.date: 2026-04-16T00:00:00.0000000Z
ms.update-cycle: 180-days
ms.topic: how-to
ms.reviewer: laarrizz
locale: en-us
document_id: 5b723a63-202b-391f-cfb3-f24849816c81
document_version_independent_id: 5b723a63-202b-391f-cfb3-f24849816c81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/monitor-device-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/monitor-device-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/monitor-device-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 20f6bd3f-fcb1-e332-cbf1-db2452b0783d
---

# See device configuration policies with Microsoft Intune - Microsoft Intune | Microsoft Learn

Intune includes some features to help monitor and manage your device configuration policies. For example, you can check the status of a policy, view the devices assigned to the policy, and update the properties of an existing policy. These capabilities extend to the profiles for your [endpoint security policies](../device-management/manage-endpoint-security-devices#review-your-profiles-for-endpoint-security-policies) for macOS and Windows devices.

You can also use [Microsoft Copilot in Intune](../copilot/) to get more information about your policies and the settings configured in your policies.

This article shows you how to check the assignment status of existing device configuration policies, make changes, troubleshoot conflicts, and how to use Copilot for some of these features.

This feature applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

## Prerequisites

At a minimum, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with one of the following roles, depending on your task:

- **Read Only Operator**: This role can view existing policies and view reports. It can't make any changes.
- **Policy and Profile manager**: This role can view existing policies and reports, and can make any changes.

For information on the built-in roles in Intune, and what they can do, go to [Role-based access control (RBAC) with Microsoft Intune](../fundamentals/role-based-access-control/overview).

## View and filter existing policies

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Policies** tab. All of your policies are shown. You also see the platform, the type of policy, and more properties.

    [![Screenshot that shows all the device configuration profiles, their profile type, and the last modified date in Microsoft Intune and Intune admin center.](media/monitor-device-profile/configuration-policy-list.png)](media/monitor-device-profile/configuration-policy-list.png#lightbox)
3. If you have many policies, you can filter by the policy type, like the settings catalog or software updates. Select **Add filters** &gt; **Policy type** &gt; **Apply**:

    ![Screenshot that shows the Add filter option to filter existing policies in Microsoft Intune and Intune admin center.](media/monitor-device-profile/filter-policies.png)

Note

For more in-depth reporting information about device configuration policies, go to [Intune reports](../device-management/reports/overview).

## View details on a policy

After you create your device configuration policy, Intune provides reporting data. These reports show the status of a policy, like it being successfully assigned to devices, or if the policy shows a conflict.

# [By policy](#tab/policy)
1. In **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Policies** tab, select an existing policy.
2. **Device and user check-in status** shows the number of all users or devices that checked-in with the policy. If one device has multiple users, this report shows the status for each user. When the user or device checks in with Intune, they receive the settings in your policy.

    The following statuses are shown:

    - **Succeeded**: The policy is applied successfully.
    - **Error**: The policy failed to apply. The message typically displays with an error code that links to an explanation.
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. An administrator should review.
    - **Pending**: The device hasn't checked in with Intune to receive the policy yet.
    - **Not applicable**: The device can't receive the policy. For example, the policy updates a setting specific to iOS 11.1, but the device is using iOS 10.
3. Select **Device assignment status**:

    ![Screenshot that shows the device assignment status report in Microsoft Intune and Intune admin center.](media/monitor-device-profile/device-assignment-status.png)

    This report shows information about the user that last checked-in. Select **Generate report** to see the latest policy assignment states for the devices that received the policy. You can also filter the assignment status to see only errors, conflicts, and more.

    It's normal for the numbers in the **Device and user check-in status** and **Device assignment status** reports to be different. The device assignment status report can take 24-48 hours to reflect recent assignment or group membership changes, especially on large tenants with many devices. Other reports depend on each device's last check-in, so devices that haven't checked-in recently can show outdated statuses.
4. Go back to **Device and user check-in status** and select **Per setting status**:

    ![Screenshot that shows the per setting status report in Microsoft Intune and Intune admin center.](media/monitor-device-profile/per-setting-status.png)

    This report shows the individual settings in the policy, and their status.
5. Go back to **Device and user check-in status** and select **View report**:

    ![Screenshot that shows to select view report on a device configuration policy to get the device and user check-in status in Microsoft Intune and Intune admin center.](media/monitor-device-profile/device-user-check-in-status-view-report.png)

    **View report** shows more information on the devices assigned to that specific device configuration policy, including:

    - The devices that received the policy
    - The user names with devices that received the policy
    - The check-in status and the last time the user/device checked in with the policy

    You can also select a specific device to get more details and use the filter column to see the assignment filter options.
6. Back in **Device and user check-in status**, the following property information for the specific policy is available for you to view and edit:

    - **Basics**: See the policy name and description.
    - **Assignments**: See the users and groups that receive policy, and see any existing [filters](../fundamentals/filters/overview) in the policy.
    - **Scope tags**: See any existing [scope tags](../fundamentals/role-based-access-control/scope-tags) used in the policy.
    - **Configuration settings**: See the settings you configured in the policy.
    - **Applicability Rules**: On your Windows devices, go to the [applicability rules](create-device-profile#applicability-rules) used in the policy.

# [Copilot](#tab/copilot-devices)
1. Go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Policies** tab &gt; select an existing policy.
2. Select **Summarize with Copilot**:

    ![Screenshot that shows you can select Summarize with Copilot on a device configuration policy in Microsoft Intune and Intune admin center.](media/monitor-device-profile/copilot-summarize-policy.png)

    The summary describes what the policy does, the users and groups assigned to the policy, and the settings in the policy. This feature can help you understand the effect of a policy and its settings on your users and devices.

    For more information on the different ways you can use Copilot in Intune, go to [Copilot in Intune overview](../copilot/).
3. Go to **Devices** &gt; **All devices** &gt; select an existing device.
4. Select **Summarize with Copilot**. Copilot shows device-specific information, like the device properties, group membership, and more.

    For information on using Copilot to troubleshoot devices, go to [Use Copilot in Intune to troubleshoot devices](../copilot/troubleshoot-devices).

---

## View details on all device configuration policies

1. Go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Monitor** tab:

    ![Screenshot that shows to select the monitor tab in device configuration profiles in Microsoft Intune and Intune admin center.](media/monitor-device-profile/device-configuration-monitor-tab.png)
2. In this area, you have access to the **Configuration policy assignment failures** report. This report helps troubleshoot errors and conflicts for configuration policies that are assigned.

    This area also provides quick access to the following reports:

    - Devices with restricted apps
    - Device encryption status
    - Certificates

Tip

In **Devices**, select **Monitor**. This area lists all reports you can use, including reports for device configuration, compliance, enrollment, and software updates. For more information on all the Intune reports, go to [Intune reports](../device-management/reports/overview).

## View conflicts

To help with conflicts, there are features in Intune to help you troubleshoot any discrepancies with the policies. When there's a conflict, you also see all the configuration policies that contain this setting.

# [By device](#tab/devices)
In **Devices** &gt; **All devices**, you can see any settings that are causing a conflict.

1. In Intune, select **Devices** &gt; **All Devices** &gt; select an existing device in the list. An end user can get the device name from their Company Portal app.
2. Select **Device configuration**. All configuration policies that apply to the device are listed.
3. Select a policy. It shows you all the settings in that policy that apply to the device.

    If a device has a **Conflict** state, select that row. In the new window, you see all the policies, and the profile names that have the setting causing the conflict.

Now that you know the conflicting setting, and the policies that include that setting, it should be easier to resolve the conflict.

# [Copilot](#tab/copilot-setting)
You can use Copilot to help troubleshoot conflicts at the setting level.

1. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; select an existing policy in the list.
2. Scroll to the **Configuration settings** area and expand a setting category:

    ![Screenshot that shows how to expand a category to see the Copilot tooltip in Microsoft Intune and Intune admin center.](media/monitor-device-profile/copilot-configuration-settings-expand-category.png)
3. For each setting, there's a Copilot tooltip:

    ![Screenshot that shows the Copilot tooltip for a setting in Microsoft Intune and Intune admin center.](media/monitor-device-profile/copilot-tooltip.png)

    Select the tooltip to get more information about setting. In Copilot Chat, enter `conflicts`. In suggestions, there are some sample prompts you can select, like **Show me policies that contain conflicting settings**.

---

## Device Firmware Configuration Interface (DFCI) profile reporting

DFCI policies are reported on a per-setting basis, just like other device configuration policies. Depending on the manufacturer's support of DFCI, some settings might not apply.

With your DFCI profile settings, you might see the following states:

- **Compliant**: This state shows when a setting value in the profile matches the setting on the device. This state can happen in the following scenarios:

    - The DFCI profile successful configured the setting in the profile.
    - The device doesn't have the hardware feature controlled by the setting, and the profile setting is **Disabled**.
    - Unified Extensible Firmware Interface (UEFI) doesn't allow DFCI to disable the feature, and the profile setting is **Enabled**.
    - The device lacks the hardware to disable the feature, and the profile setting is **Enabled**.
- **Not Applicable**: This state shows when a setting value in the profile is **Enabled** or **Allowed**, and the matching setting on the device isn't found. This state can happen if the device hardware doesn't have the feature.
- **Noncompliant**: This state shows when a setting value in the profile doesn't match the setting on the device. This state can happen in the following scenarios:

    - UEFI doesn't allow DFCI to disable a setting, and the profile setting is **Disabled**.
    - The device lacks the hardware to disable the feature, and the profile setting is **Disabled**.
    - The device doesn't have the latest DFCI firmware version.
    - DFCI was disabled before being enrolled in Intune using a local "opt-out" control in the UEFI menu.
    - The device was enrolled to Intune outside of Windows Autopilot enrollment.
    - The device isn't registered to Windows Autopilot by a Microsoft CSP, or registered directly by the OEM.