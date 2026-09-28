---
layout: Conceptual
title: Get started with iOS/iPadOS frontline worker devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/frontline-worker/ios-ipados
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to manage frontline worker devices using iOS and iPadOS devices in Microsoft Intune. Select the best enrollment option, configure the home screen, and more.
ms.date: 2024-03-28T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: cbernier
locale: en-us
document_id: 2db06731-0053-4527-4c33-327e151c2998
document_version_independent_id: 2db06731-0053-4527-4c33-327e151c2998
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/frontline-worker/ios-ipados.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/frontline-worker/ios-ipados
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/frontline-worker/ios-ipados.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 8a7ab696-3de8-006b-eff1-8a7b237f8bfb
---

# Get started with iOS/iPadOS frontline worker devices - Microsoft Intune | Microsoft Learn

iPad devices are a popular device type for frontline workers (FLW). They're used in different scenarios and industries, including field operations, healthcare, aviation, warehouse, data entry, digital forms, and presentations.

For iPadOS FLW devices, you can use the **Shared iPad** feature in Intune or use **Microsoft Entra shared device mode** (SDM). For more information, go to Shared iPad vs Microsoft Entra shared device mode (in this article).

iOS devices can also be used for FLW, but it's not common. For iOS FLW devices, we recommended you use [Microsoft Entra shared device mode](/en-us/azure/active-directory/develop/msal-ios-shared-devices) and Intune together. In Intune, you enroll the device and create a device restrictions configuration profile. In the Intune profile, you can allow (or prohibit) specific apps, and can hide apps.

The following diagram shows the iOS/iPadOS options for frontline worker devices in Intune:

[![Diagram that shows Apple iOS and iPadOS frontline worker scenario path in Microsoft Intune.](media/ios-ipados/flw-options.png)](media/ios-ipados/flw-options.png#lightbox)

The **Shared iPad** feature in Intune is designed for frontline workers. Since iPads are a popular Apple device type for frontline workers (FLW), **this article focuses on iPad devices**.

Use this article to get started with iPad FLW devices in Intune. It includes decisions admins need to make, determining how the device is used, and configuring the home screen & device experience. Specifically:

- Shared iPad vs. Microsoft Entra shared device mode
- Step 1 - Enroll, enable Shared iPad, and choose a temporary session type
- Step 2 - Home screen layout and device experience

This article applies to:

- iPadOS devices owned by the organization and enrolled in Intune

For an overview on FLW devices in Intune, go to [FLW device management in Intune](./).

Note

There are other iOS/iPadOS enrollment options available. This article focuses on the enrollment options commonly used for FLW devices. For more information on all the iOS/iPadOS enrollment options, go to [Enrollment guide: Enroll iOS and iPadOS devices in Microsoft Intune](../../device-enrollment/apple/guide-ios-ipados).

## Shared iPad vs Microsoft Entra shared device mode

For FLW iPad devices, there are two options available - **Shared iPad in Intune** or **Microsoft Entra shared device mode**. For iPad devices, admins must pick one option. This decision impacts how you configure the device.

[![Diagram that shows all the Shared iPad and Entra shared device mode options for iPadOS frontline worker devices in Microsoft Intune.](media/ios-ipados/enrollment-options.png)](media/ios-ipados/enrollment-options.png#lightbox)

When using iPad devices for FLW, use the following information to help you decide which option is best for your organization:

# [Shared iPad](#tab/sharedipad)
Shared iPads are a feature in Intune, and are the recommended and preferred device type for frontline worker devices. These devices are shared among many users, such as in a hospital or school. Each user has their own profile and data, and they can sign in and out of the device.

![](../../media/icons/16/check.svg) If the device is an iPad, then use the Shared iPad feature in Intune. For more information on Shared iPads in Intune, go to [Shared iPad devices in Intune](../../device-enrollment/apple/shared-ipad).

![](../../media/icons/16/error.svg) If the device is an iOS device, then use Entra shared device mode. For more information, go to [Microsoft Entra shared device mode for FLW](./#microsoft-entra-shared-device-mode-for-flw) and [Shared device mode for iOS devices](/en-us/azure/active-directory/develop/msal-ios-shared-devices).

Note

For iPadOS devices, Conditional Access isn't supported for Shared iPad. For more information, go to [Overview of shared device solutions for iOS/iPadOS](../../device-enrollment/apple/shared-device-solutions-ios).

# [Entra shared device mode](#tab/entrasdm)
Microsoft Entra shared device mode (SDM) is an option for iOS and iPadOS devices and uses the [Microsoft Enterprise SSO plug-in for Apple devices](/en-us/azure/active-directory/develop/apple-sso-plugin). Entra SDM offers an app and identity driven sign in/sign out experience, which improves the end user experience and productivity (less sign in prompts). Entra shared device mode isn't supported with Shared iPad feature in Intune.

For more information on Entra shared device mode (SDM), go to [Microsoft Entra shared device mode for FLW](./#microsoft-entra-shared-device-mode-for-flw).

When to use Entra SDM:

![](../../media/icons/16/check.svg) If the device is an iOS device, then use Entra shared device mode.

![](../../media/icons/16/check.svg) If the device is an iPad, then you can use Entra shared device mode **OR** Shared iPad in Intune.

![](../../media/icons/16/error.svg) If you configured an iPad to be a Shared iPad in Intune, then don't use Entra shared device mode. It's not supported.

For end users to have the full sign in/sign out experience, apps must support Entra SDM. For more information on Entra SDM and iOS/iPadOS devices, go to:

- [Shared device mode for iOS devices](/en-us/azure/active-directory/develop/msal-ios-shared-devices)
- [Set up automated device enrollment for shared device mode](../../device-enrollment/apple/setup-automated-shared-device-mode)

---

Tip

For a more detailed comparison of both options, go to [Shared iOS and iPadOS devices](../../device-enrollment/apple/shared-device-solutions-ios).

## Step 1 - Enroll, enable Shared iPad, and choose a temporary session type

For Shared iPad FLW devices, the first step is to create an **Automated Device Enrollment (ADE) profile**. ADE is the required enrollment option for Shared iPads. ADE syncs the devices from Apple Business or Apple School Manager.

From an Intune perspective, you configure the enrollment profile and assign the profile to the device. When you create the enrollment profile for Shared iPads, you select the following features:

1. **Enroll without user affinity**: This option doesn't associate the devices with a specific user. This option is required for Shared iPads.
2. **Shared iPad**: This option enables Shared iPad on the device, and is required. It allows many users to sign in to the device.
3. **Require Shared iPad temporary session**: This setting determines if the Shared iPads are used for guest access. Your options:

    - **Guest access**

        **Yes** enables temporary sessions. Users sign in to the device as a guest. They don't enter a Managed Apple ID or password. When the user signs out, all user data, sign in info, and browsing history are deleted.

        For example, in healthcare, a medical patient is assigned a shared iPad to check in or fill out forms. When they're done, they sign out and all their local user data is deleted from the device. The next patient can then sign in to the device as a guest and use the device.
    - **Partitioned user access**

        Partitioned user access is the default behavior for Shared iPads. In Intune, **Not configured** uses this default behavior. Use this option when an iPad is used by many authenticated users at different times.

        Each user signs in to the device with their federated Entra credentials. User partitions ensure that each user's apps, data, and preferences are stored separately on the iPad. Only the same set of apps used across all device users support partitioned user access.

        When the user locks their profile, their data remains on the device in their own partition. Then, the device is ready for the next user to sign in and use the device.

        The number of users that can sign in also varies by the amount of storage on the device. So, we recommended you plan accordingly and configure the enrollment profile to accommodate your needs.

The following image shows a sample Shared iPad enrollment policy in Intune that enables guest access:

[![An Automated Device Enrollment (ADE) policy with Shared iPad enabled, and temporary sessions for Shared iPadOS enabled for frontline worker devices in Microsoft Intune.](media/ios-ipados/shared-ipad-ade-enrollment-policy.png)](media/ios-ipados/shared-ipad-ade-enrollment-policy.png#lightbox)

For more information on these features, and to get started, go to:

- [Set up automated device enrollment in Intune](../../device-enrollment/apple/setup-automated-ios)
- [Set up Shared iPad in Intune](../../device-enrollment/apple/shared-ipad)

## Step 2 - Home screen layout and device experience

For Shared iPad FLW devices, next consider what end users do on the devices and the device experience they need for their jobs. This decision impacts how you configure the device.

In Intune, you can create device configuration profiles that configure the home screen and the apps that are shown. Specifically, you create a:

- **Device features** policy to configure the home screen layout and other settings you want to apply to the device:

    [![A device features policy with the home screen layout settings configured for iOS and iPadOS device in Microsoft Intune.](media/ios-ipados/home-screen-layout.png)](media/ios-ipados/home-screen-layout.png#lightbox)
- **Device restrictions** policy to configure other device settings, such as using kiosk mode and other settings you want to apply to the device:

    [![A device restrictions policy with the device settings configured for iOS and iPadOS devices in Microsoft Intune.](media/ios-ipados/device-restrictions-kiosk.png)](media/ios-ipados/device-restrictions-kiosk.png#lightbox)

    In this policy, you can also create a list of approved apps and hide some system apps. For more information on the settings you can configure, go to [iOS and iPadOS device settings to allow or restrict features using Intune](../../device-configuration/templates/ref-device-restrictions-apple).

For a list of the Shared iPad settings you can configure, go to [Configure settings for Shared iPads](../../device-enrollment/apple/shared-ipad#configure-settings-for-shared-ipads).

For a list of all the device configuration settings, go to:

- [iOS and iPadOS device settings to use common features](../../device-configuration/templates/ref-device-features-apple)
- [iOS and iPadOS device settings to allow or restrict features](../../device-configuration/templates/ref-device-restrictions-apple)