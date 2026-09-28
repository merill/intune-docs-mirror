---
layout: Conceptual
title: Configure device configuration profiles in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile
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
description: Add or configure a device configuration profile in Microsoft Intune. Select the platform type, configure the settings, and add a scope tag. Learn more about applicability rules, and the policy refresh cycle times.
ms.date: 2025-09-15T00:00:00.0000000Z
ms.update-cycle: 180-days
ms.topic: how-to
ms.reviewer: 
locale: en-us
document_id: df3dbd37-b8d8-b10c-2582-d38d0457a62f
document_version_independent_id: df3dbd37-b8d8-b10c-2582-d38d0457a62f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/create-device-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/create-device-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/create-device-profile.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 96ba65be-eef1-9100-ce03-789fc7c36462
---

# Configure device configuration profiles in Microsoft Intune - Microsoft Intune | Microsoft Learn

Device configuration profiles allow you to add and configure device settings, and then push these settings to devices in your organization. You have some options when creating policies:

- **Baselines**: On Windows devices, these baselines include preconfigured security settings. If you want to create security policy using recommendations by Microsoft security teams, then use security baselines.

    For more information, go to [Security baselines](../device-security/security-baselines/overview).
- **Settings catalog**: On your Apple, Android, and Windows devices, you can use the settings catalog to configure device features and settings. The settings catalog has all the available settings, and in one location. For example, you can see all the settings that apply to BitLocker, and create a policy that just focuses on BitLocker. On macOS devices, use the settings catalog to configure Microsoft Edge version 77 and settings.

    More settings are continually being added to the settings catalog. For more information, go to [Settings catalog](settings-catalog/).
- **Templates**: On your devices, you can use the built-in templates. Each template includes a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. If you're familiar with creating device configuration policies in Microsoft Intune, then you're already using these templates.

    For more information, including the available templates, go to [Apply features and settings on your devices using device profiles](overview).

This article:

- Lists the steps to create a profile.
- Shows you how to add a scope tag to "filter" your policies.
- Describes applicability rules on Windows client devices, and shows you how to create a rule.
- Has more information on the check-in refresh cycle times when devices receive profiles and any profile updates.

This feature applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

## Prerequisites

- At a minimum, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control (RBAC) with Microsoft Intune](../fundamentals/role-based-access-control/overview).
- Enroll your devices in Intune. To learn more about your enrollment options, see [Microsoft Intune enrollment guide](../device-enrollment/guide).

## Create the profile

In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices**. You have the following options:

[![Screenshot that shows how to select Devices to see what you can configure and manage in Microsoft Intune.](media/create-device-profile/devices-overview.png)](media/create-device-profile/devices-overview.png#lightbox)

- **Overview**: Lists the status of some of your profiles, and provides more details on the profiles you assigned to users and devices.
- **Monitor**: Lists all device monitoring reports. Use these reports to check configuration policy assignment failures, incomplete user enrollments, noncompliant devices, update installation failures, and more.
- **By platform**: Expand this option to get a list of supported platforms, like Android and Linux. When you select a platform, you can create and view policies and profiles for the platform you choose.

    This view can also show features specific to the platform. For example, select **Windows**. You see Windows-specific features, like **Scripts and remediations** and **Group policy analytics**.
- **Manage devices**: Expand this option to see the policies you can create, like compliance and configuration policies.

When you create a profile (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**), choose your platform:

- **Android device administrator**
- **Android (AOSP)**
- **Android Enterprise**
- **iOS/iPadOS**
- **macOS**
- **Windows 10 and later**
- **Windows 8.1 and later**

Then, choose your profile type. Depending on the platform you choose, the profile types are different. The following articles describe the different profiles:

# [Settings catalog](#tab/sc)
- [Settings catalog](settings-catalog/) - Includes a list of all available settings for Android Enterprise, iOS/iPadOS, macOS, and Windows. You can search and filter on specific settings and areas, like OneDrive or Microsoft Edge.

# [Properties catalog](#tab/prop)
- [Properties catalog](collect-device-properties) - Includes a list of available device properties for Windows devices, like CPU manufacturer, network adapter identifier, and more.

# [Templates](#tab/templates)
Each template is a logical group of settings grouped together, like Email, VPN, and Wi-Fi.

- [BIOS configuration and other settings](templates/configure-bios-windows)
- [Custom](templates/configure-custom-settings)
- [Delivery Optimization (Windows)](templates/configure-delivery-optimization-windows)
- [Derived credential (Android Enterprise, iOS, iPadOS)](../device-security/certificates/derived-credentials)
- [Device features (macOS, iOS, iPadOS)](templates/configure-device-features-apple)
- [Device firmware configuration interface (DFCI) (Windows)](templates/configure-dfci-windows)
- [Device restrictions](templates/configure-device-restrictions)
- [Domain join (Windows)](templates/configure-domain-join-windows)
- [Edition upgrade and mode switch (Windows)](templates/configure-edition-upgrade-windows)
- [Education (iOS, iPadOS)](../solutions/education/ref-classroom-settings-ios)
- [Email](templates/configure-email)
- [Endpoint protection (macOS, Windows)](endpoint-security/configure-endpoint-protection)
- [Extensions (macOS)](templates/configure-kernel-extensions-macos)
- [Kiosk](templates/configure-kiosk)
- [Microsoft Defender for Endpoint (Windows)](../device-security/microsoft-defender/overview)
- [Mobility Extensions (MX) profile (Android device administrator)](templates/configure-zebra-mx-android)
- [Network boundary (Windows)](templates/create-network-boundary-windows)
- [OEMConfig (Android Enterprise)](templates/configure-oemconfig-android)
- [PKCS certificate](certificates/pkcs-profiles)
- [PKCS imported certificate](certificates/imported-pfx-profiles)
- [Preference file (macOS)](templates/configure-preference-file-macos)
- [SCEP certificate](../fundamentals/certificates/scep-infrastructure)
- [Secure assessment (Education) (Windows)](templates/configure-education-settings)
- [Shared multi-user device (Windows)](templates/configure-shared-device)
- [Trusted certificate](../fundamentals/certificates/overview)
- [VPN](templates/configure-vpn)
- [Wi-Fi](templates/configure-wifi)
- [Windows health monitoring](templates/configure-health-monitoring-windows)
- [Wired networks](templates/configure-wired-networks)

---

For example, if you select Windows for the platform, your options look similar to the following profile:

![Screenshot that shows how to create a Windows device configuration policy and profile in Microsoft Intune.](media/create-device-profile/windows-create-device-profile.png)

## Scope tags

After you add the settings, you can also add a scope tag to the profile. Scope tags filter profiles to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. And, are used in distributed IT.

For more information about scope tags, and what you can do, go to [Use RBAC and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).

## Applicability rules

Applies to:

- Windows

Applicability rules allow administrators to target devices in a group that meet specific criteria. For example, you create a device restrictions profile that applies to the **All Windows devices** group. And, you only want the profile assigned to devices running Windows Enterprise.

To do this task, create an **applicability rule**. These rules are great for the following scenarios:

- At Bellows College, you want to target all Windows devices running Windows 11, version 24H2.
- You want to target all users in Human Resources at Contoso, but only want Windows Professional or Enterprise devices.

To approach these scenarios, you:

- Create a devices group that includes all devices at Bellows College. In the profile, add an applicability rule so it applies if the OS minimum version is `10.0.26100` and the maximum version is `10.0.26200`. Assign this profile to the Bellows College devices group.

    When the profile is assigned, it applies to devices between the minimum and maximum versions you enter. For devices that aren't between the minimum and maximum versions you enter, their status shows as **Not applicable**.
- Create a users group that includes all users in Human Resources (HR) at Contoso. In the profile, add an applicability rule so it applies to devices running Windows Professional or Enterprise. Assign this profile to the HR users group.

    When the profile is assigned, it applies to devices running Windows Professional or Enterprise. For devices that aren't running these editions, their status shows as **Not applicable**.
- If there are two profiles with the exact same settings, then the profile without an applicability rule is applied.

    For example, ProfileA targets the Windows devices group, enables BitLocker, and doesn't have an applicability rule. ProfileB targets the same Windows devices group, enables BitLocker, and has an applicability rule to only apply the profile to the Windows Enterprise edition.

    When both profiles are assigned, ProfileA is applied because it doesn't have an applicability rule.

When you assign the profile to the groups, the applicability rules act as a filter, and only target the devices that meet your criteria.

### Add a rule

Use the following steps to create an applicability rule.

1. In your policy, select **Applicability Rules**. You can choose the **Rule**, and **Property**:

    [![Screenshot that shows how to add an applicability rule to a Windows device configuration profile in Microsoft Intune.](media/create-device-profile/applicability-rules.png)](media/create-device-profile/applicability-rules.png#lightbox)
2. In **Rule**, choose if you want to include or exclude users or groups. Your options:

    - **Assign profile if**: Includes users or groups that meet the criteria you enter.
    - **Don't assign profile if**: Excludes users or groups that meet the criteria you enter.
3. In **Property**, choose your filter. Your options:

    - **OS edition**: In the list, check the Windows client editions you want to include (or exclude) in your rule.
    - **OS version**: Enter the **min** and **max** Windows client version numbers of you want to include (or exclude) in your rule. Both values are required.

        For example, you can enter `10.0.16299.0` (RS3 or 1709) for minimum version and `10.0.17134.0` (RS4 or 1803) for maximum version. Or, you can be more granular and enter `10.0.16299.001` for minimum version and `10.0.17134.319` for maximum version.

        For more version numbers, go to [Windows client release information](/en-us/windows/release-health/release-information).
4. Select **Add** to save your changes.

## Policy refresh cycle times

Intune uses different refresh cycles to check for updates to configuration profiles. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](troubleshoot-device-profiles#policy-refresh-intervals) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for profile updates.

## Recommendations

When creating profiles, consider the following recommendations:

- Name your policies so you know what they are, and what they do. All [compliance policies](../device-security/compliance/create-policy) and [configuration profiles](create-device-profile) have an optional **Description** property. In **Description**, be specific and include information so others know what the policy does.

    Some configuration profile examples include:

    **Profile name**: OneDrive configuration profile for all Windows users**Profile description**: OneDrive profile that includes the minimum and base settings for all Windows users. Created by `user@contoso.com` to prevent users from sharing organizational data to personal OneDrive accounts.

    **Profile name**: VPN profile for all iOS/iPadOS users**Profile description**: VPN profile that includes the minimum and base settings for all iOS/iPadOS users to connect to Contoso VPN. Created by `user@contoso.com` so users automatically authenticate to VPN, instead of prompting users for their username and password.
- Create your profile by its task, such as configure Microsoft Edge settings, enable Microsoft Defender anti-virus settings, block iOS/iPadOS jailbroken devices, and so on.
- Create profiles that apply to specific groups, such as Marketing, Sales, IT Administrators, or by location or school system. Use the built-in features, including:

    - [Use role-based access control (RBAC) and scope tags for distributed IT in Intune](../fundamentals/role-based-access-control/scope-tags)
    - [Distributed IT with many admins in the same Intune tenant](../fundamentals/scale-guidelines)
    - [Use filters when assigning your apps, policies, and profiles in Intune](../fundamentals/filters/overview)
- Separate user policies from device policies.

    For example, the [Intune settings catalog](settings-catalog/) has thousands of settings. These settings show if a setting applies to users or devices. When creating the policy, assign your user settings to a users group, and assign your device settings to a devices group.

    The following image shows an example of some settings that can apply to users, apply to devices, or apply to both:

    [![Screenshot that shows an Intune admin template that applies to user and devices in Microsoft Intune.](media/create-device-profile/setting-applies-to-user-and-device.png)](media/create-device-profile/setting-applies-to-user-and-device.png#lightbox)
- Use Microsoft Copilot in Intune to evaluate your policies, learn more about a policy setting & its effect on your users & security, and compare policies between two devices.

    For more information, go to [Microsoft Copilot in Intune](../copilot/).
- Every time you create a restrictive policy, communicate this change to your users. For example, if you're changing the passcode requirement from four (4) characters to six (6) characters, let your users know before your assign the policy.