---
layout: Conceptual
title: Enroll personal devices in Intune with Android Enterprise work profile management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-personal-work-profile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Set up Intune for personal devices and bring-your-own-device scenarios using Android Enterprise work profile management.
ms.date: 2026-06-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilso
locale: en-us
document_id: 816a3659-6de8-8cba-8ccf-39d4813ced0e
document_version_independent_id: 816a3659-6de8-8cba-8ccf-39d4813ced0e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/setup-personal-work-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/setup-personal-work-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/setup-personal-work-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 0213dfbb-4a7e-44de-f999-94e08365a123
---

# Enroll personal devices in Intune with Android Enterprise work profile management - Microsoft Intune | Microsoft Learn

Set up enrollment for bring-your-own-device (BYOD) and personal device scenarios using the *Android Enterprise personally owned work profile* management solution. During enrollment, a work profile is created on the device to house work apps and work data. You can use Microsoft Intune policies to manage the work profile and its contents. Personal apps and data stay separate in another part of the device and remain unaffected by Intune.

For more information about Android Enterprise work profile features, see [Work profiles](https://support.google.com/work/android/answer/9563584) (opens Android Enterprise Help).

## Enrollment methods

Important

Intune is transitioning personally owned work profile management to web-based enrollment. To opt in, enable web-based enrollment for new devices and deploy the Move to Android Management API policy for existing enrolled devices. For more information, see [Android Management API for personally owned work profiles](android-management-api-overview).

Intune supports two enrollment methods for personally owned work profile devices. Use the following table to understand your options and migration path.

| Enrollment method | Policy delivery | How initiated | Status |
| --- | --- | --- | --- |
| Company Portal app | Custom DPC | Company Portal app | Being phased out. Migrates to web-based enrollment when enabled. |
| Web-based enrollment | Android Management API | Browser (URL/redirect) | Default for new tenants and after migration from Custom DPC. Company Portal not required for enrollment. |

## Requirements

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Confirm Android Enterprise availability in your country/region. For more information, see [Is Android Enterprise available in my country/region?](https://support.google.com/work/android/answer/6270910).

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> [Connect your Intune tenant account to your Android Enterprise account](connect-managed-google-play).

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Make sure Android Enterprise is supported on devices. For more information, see:
> 
> - [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&amp;ref_topic=6151012) (opens Google support)
> - [Android Enterprise help - General FAQs](https://support.google.com/work/android/answer/14772109?hl=en#zippy=%2cif-my-device-is-not-android-enterprise-recommended-aer-can-i-still-use-android-enterprise)
> - [Check & fix Play Protect certification status](https://support.google.com/googleplay/answer/7165974?hl=en#zippy=%2Cdevice-isnt-certified)
> 

Note

Web-based enrollment currently requires Chrome, Edge or Samsung browser. Other browsers might not support all enrollment steps.

## Set up enrollment

Complete these steps to set up enrollment for Android Enterprise devices in BYOD scenarios. Whether users enroll through the web-based flow or through the Company Portal app, you first create an enrollment profile. Web-based enrollment is the recommended method and requires an extra step within the profile to enable it. For app-based enrollment through Company Portal, create the same enrollment profile, but don't select the web enrollment option. Configuring device platform restrictions is optional and only needed if you want to restrict or customize enrollment behavior beyond the defaults.

Note

Device enrollment managers can enroll up to 10 devices per account.

### Create an enrollment profile

Create an enrollment profile for personally owned work profile devices. The same profile supports both web-based and Company Portal app-based enrollment. Enabling web enrollment is just one additional step within it.

Note

If passkeys are configured as the only accepted authentication method in your tenant, don't enable web enrollment until passkey support for web enrollment is announced.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Device onboarding** and select **Enrollment**.
4. Select the **Android** tab.
5. Under **Enrollment Profiles**, select **Personally owned devices with a work profile**.
6. Select **Use web enrollment for all users enrolling into Android personally owned work profile management** to enable web-based enrollment. If passkeys are your only authentication method, leave this unselected and rely on Company Portal app-based enrollment instead.
7. Select **Save**. Enabling web-based enrollment applies at the tenant level and can't be reversed.

### Configure device platform restrictions

Use this section only if you need to control or restrict other enrollment methods, such as blocking Android device administrator enrollment. If the default settings meet your needs, skip this step.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Device onboarding** and select **Enrollment**.
4. Select the **Android** tab.
5. In the **Enrollment options** section, choose **Device platform restriction**.
6. Select the **Android restrictions** tab.
7. Select **Create restriction**.
8. On the **Basics** page, enter a name and description for the restriction so that you can distinguish it from other restrictions in the admin center. Device users don't see these details.
9. Select **Next** to continue to **Platform settings**.
10. Configure platform settings for **Android Enterprise (work profile)**. Your options:

    - **Platform**: Select **Allow** to permit enrollment with Android Enterprise work profile. Select **Block** to prevent work profile enrollment. If you block work profile, devices enroll using the Android device administrator management solution, unless device administrator enrollment is also blocked.
    - **Personally owned**: Select **Allow** to permit personal devices to enroll with a work profile. Personal devices are allowed by default. Select **Block** to prevent personal devices from enrolling with a work profile. Android devices that don't support Android Enterprise enroll using the Android device administrator solution, unless device administrator enrollment is blocked.

    Important

    The **Personally owned** setting configured as **Block** doesn't apply to [Android Management API (AMAPI)](android-management-api-overview) devices and isn't reliable for devices running Android 12 and later that use Custom DPC enrollment. If you're using this setting to prevent personally owned work profile enrollment, consider one of the following alternatives:

    - Use a corporate-owned management method: Enroll devices as [corporate-owned work profile](setup-corporate-work-profile) devices instead of personally owned.
    - Restrict enrollment by user group: Configure the enrollment restriction to block Android Enterprise work profile enrollment for all users. Then create a higher-priority restriction that allows enrollment for an approved group only. This approach controls enrollment through group membership instead of the **Personally owned** setting.

    Any device that supports Android Enterprise personal work profiles also supports the Android device administrator management solution, so if you don't want Android device administrator to be a part of enrollments, make sure to block the platform. For more information, see [device platform restrictions](../create-platform-restrictions#best-practice---android-platform-restrictions).

    Note

    Today, Android Enterprise work profile management for personal devices is allowed by default. In policies configured before July 2019 without any changes, the default setting blocks Android Enterprise work profile management.

    Important

    Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).
11. Select **Next** to continue to **Scope tags**.
12. If needed, apply one or more scope tags to limit visibility and management of restrictions to certain admin users in Intune. For more information about how to use scope tags, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
13. Select **Next** to continue to **Assignments**.
14. Assign the restriction to all users, or select specific groups.
15. Select **Next** to continue to **Review + create**.
16. Review your choices, and then select **Create** to finish creating the restriction.

## Enroll devices

When web-based enrollment is enabled, users can access enrollment from any of the following entry points, all of which launch the same enrollment webpage:

- Productivity apps such as Teams or Outlook (recommended): If you've configured conditional access policies that require enrollment before accessing corporate resources, users are prompted to enroll when they open a supported app.
- Company Portal app: Users can open the Company Portal app and follow the prompts to enroll.
- Enrollment URL: Users can go to https://aka.ms/enrollmyandroid in their browser to start enrollment.

Be sure to communicate which entry point your organization uses, along with clear guidance on the enrollment steps and what information to enter. Users might be unfamiliar with self-enrollment or with the Intune Company Portal and Microsoft Intune apps. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](../../fundamentals/planning-guide#step-5---create-a-rollout-plan).

Users must be signed in to the primary user account on their device when enrolling. Enrollment isn't supported on secondary user accounts. Personal devices previously enrolled with Android device administrator can unenroll, and then re-enroll using the work profile solution.

Tip

You can remotely return a device to a state where it's ready to enroll again by using the **Retire** function in the admin center. For more information, see [Remote device action: retire](../../device-management/actions/retire?pivots=android).

For more information and screenshots of the end user experience, see [Enroll device with Android work profile](../../user-help/enrollment/enroll-work-profile-android) in the Intune user help docs.

## Apps installed at enrollment

Intune automatically installs the following apps on enrolled devices:

- Microsoft Intune: User-facing app for device management tasks, including checking compliance, syncing policies, collecting diagnostic logs, and contacting IT support.
- Company Portal: Used for browsing and installing work apps and supports MAM scenarios.
- Android Device Policy: Enforces Android Management API policies on web-based enrollments. Installed in a hidden state. Users don't see it.
- Microsoft Authenticator: Provides single sign-on (SSO) for the user's work account.

## Data shared with Google

Microsoft Intune shares certain user and device information with Google when Android Enterprise device management is enabled. For more information, see [Data Intune sends to Google](../../privacy/data-sharing/ref-intune-to-google).

## Limitations

The limitations in this section apply to personal devices with a work profile.

### Private space

Private space is a feature introduced with Android 15 that lets people create a space on their device for sensitive apps and data they want to keep hidden.

- The private space is considered a personal profile. Microsoft Intune doesn't support mobile device management within the private space or provide technical support for devices that attempt to enroll the private space.
- If users attempt to enroll the private space after they enroll the device, Intune will initiate the device administrator enrollment process. The second enrollment causes two enrollment records to appear in the Microsoft Intune admin center: one under work profile management and one under device administrator management. Microsoft Intune doesn't provide support for this scenario.

### Web-based enrollment

- If passkeys are configured as the only accepted authentication method in your tenant, users can't complete web enrollment. Don't enable web enrollment until passkey support is announced.
- Microsoft Teams and Outlook are the supported productivity app entry points for web enrollment. Other Microsoft 365 apps aren't currently supported as enrollment entry points.
- Microsoft Entra Terms of Use (TOU) before work profile creation aren't supported for Android web enrollment without also requiring them across all Intune scenarios.
- After web enrollment, both the Microsoft Intune app (for device management) and Company Portal (for app management) are installed in the work profile of the device. If Company Portal isn't visible, verify it was installed successfully.
- If a user is already enrolled with an older Custom DPC work profile and opens a productivity app in their personal profile after web enrollment is enabled but before their device is migrated, they might be prompted to enroll again. Attempting to re-enroll results in an error. Direct these users to open the productivity app in their work profile instead.
- If a user lands on the **Get Started** enrollment page but their device is already enrolled, they might only need to redo Workplace Join. For more information, see [Redo Workplace Join for Android Enterprise devices](redo-workplace-join-android).
- If Company Portal is older than version 2604.x, users are routed to the app-based enrollment flow instead of web-based enrollment. Ensure Company Portal is up to date on devices before enabling web-based enrollment.
- During enrollment, the browser might prompt users to add their work account to the browser. Users should skip this prompt and continue with the enrollment steps.