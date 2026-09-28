---
layout: Conceptual
title: Control AI features on Android Enterprise devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/ai/manage-ai-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Using Microsoft Intune, you can manage and restrict AI usage on Android devices enrolled in Intune. This guide provides lists the steps in Intune to block AI apps, websites, screen-driven experiences, on-device AI services, and OEM-specific AI features. You can manage Microsoft Copilot, Google Gemini, Samsung Galaxy AI, claude.ai, ChatGPT, and more.
ms.date: 2025-11-11T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: cchristenson
ms.collection:
- M365-identity-device-management
- intune-scenario
locale: en-us
document_id: 41d3665f-c873-294a-5294-386b42dde6a0
document_version_independent_id: 41d3665f-c873-294a-5294-386b42dde6a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/ai/manage-ai-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/ai/manage-ai-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/ai/manage-ai-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: bc72fa4d-edb4-0332-36a9-5abe51391925
---

# Control AI features on Android Enterprise devices - Microsoft Intune | Microsoft Learn

In Microsoft Intune, you can manage and restrict generative AI usage on Android devices enrolled in Intune. You can block (or allow) AI apps, websites, screen-driven experiences, on-device AI services, and OEM-specific AI features.

This article lists different ways that AI experiences can be available on Android devices, and how you can use Intune to block these experiences.

When you use the steps in this guide, you can manage and restrict AI experiences on your Android devices.

Applies to:

- Android Enterprise

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> IT admins and security engineers can allow/block generative AI on the following Android enrollment types:
> 
> - Android Enterprise corporate owned fully managed devices (COBO)
> - Android Enterprise corporate owned dedicated devices (COSU)
> - Android Enterprise corporate owned devices with a work profile (COPE)
> - Android Enterprise personally owned devices with a work profile (BYOD)
> 
> 
> To learn more about the different Android enrollment options, see the [Android Enrollment guide](../../device-enrollment/android/guide).

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Devices enrolled in Intune, including co-managed devices
> - Managed Google Play account linked in the Intune admin center (**Devices &gt; Android &gt; Enrollment &gt; Managed Google Play**)
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure the policies, use an account with the following role:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

## Before you begin

- When you create the AI policies, you can assign them to the **All Users** and **All Devices** groups. Even though this assignment is the simplest approach, you can target your policies to specific users and devices.

    To learn more, see:

    - [Inclusion and exclusion groups](../../app-management/deployment/configure-assignment-scope) to assign apps that target specific users and devices.
    - [Assign policies in Intune](../../device-configuration/assign-device-profile) that target specific users and devices.
- For corporate owned devices with a work profile (COPE) and personally owned devices with a work profile (BYOD), most controls are available only in the work profile. They're not available in the personal profile.
- The steps in this guide show you how to block AI experiences. If you want to allow specific AI experiences, you can use the same steps but configure them to allow instead of block.
- When you create a policy and assign it, the devices receive the policy the next time they check in with Intune. To learn more, see [Intune policy refresh intervals](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

## How AI shows up on Android

On Android devices, AI is available in several ways:

- **AI apps** - Standalone apps like ChatGPT, Microsoft Copilot, and Perplexity can be downloaded and used on the devices.
- **AI websites** - Users can access AI websites through browser apps, like Microsoft Edge and Chrome.
- **Screen-driven and Assistant experiences** - OS-integrated features that read on-screen content (like Circle to Search) or provide assistant help are typically installed and available by default.
- **On-device AI services** - Android can run the on-device **Gemini Nano** foundational model locally using **AICore**. Apps like Messages, Recorder, or GBoard use Gemini Nano to respond to messages, generate summaries, and suggest smart replies.
- **OEM-specific AI services** - OEMs might implement their own AI capabilities, like Galaxy AI by Samsung.

## Block AI apps

![](../../media/icons/16/check.svg)**Goal - End users can't install AI apps from the Google Play Store**

AI apps like ChatGPT, Copilot, Perplexity, and Claude can be installed from the Google Play Store. You can use Intune to block these apps from being installed on your devices.

# [Corporate owned devices](#tab/ai-apps-corp)
**Supported enrollment types**:

- Corporate owned fully managed devices (COBO)
- Corporate owned dedicated devices (COSU)
- Corporate owned devices with a work profile (COPE)

### Step 1 - Determine your app strategy

Determine your organization's app strategy - **Block or Allow**:

- **Block strategy** - No apps in the Google Play Store can be downloaded unless assigned by admins. Only apps that are assigned are available on the device.

    This strategy is the default for corporate owned devices.
- **Allow strategy** - All apps can be downloaded unless specifically blocked by admins.

    If the following setting is set to **Allow** in a device restrictions configuration profile, then your organization is probably using an Allow strategy. This setting allows non-admin specified apps to be downloaded:

    - **Devices** &gt; **Android Enterprise** &gt; **Configuration** &gt; **Create** &gt; **New Policy** &gt; **Templates** &gt; **Device Restrictions** &gt; **Applications** &gt; **Allow access to all apps in Google Play store**

### Step 2 - Implement your app strategy

In this step, implement your app strategy to block or allow AI apps.

#### Block strategy (default)

With a Block strategy, no apps in the Google Play Store can be downloaded unless explicitly allowed. Use the following steps to make sure the app you want to block isn't already deployed to your devices.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Android apps**.
2. Select the app name &gt; **Properties**.
3. Make sure **Assignments** is not set to **Required**, not set to **Available for enrolled devices**, or not set to **Available with or without enrollment**.

If all these options aren't set, then the app hasn't been deployed by an Intune policy. If any of these options are set, then the app is deployed. In this scenario, you can change the assignment to **Uninstall** to remove it from the devices.

#### Allow strategy

With an Allow strategy, all apps in the Google Play Store can be downloaded.

1. Determine if the **Allow access to all apps in Google Play store** setting is set to allow.

    If you use [Copilot](../../copilot/), you can ask Copilot to check this setting for you. You can also create a new device restrictions profile to configure this setting.

    1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Configuration** &gt; **Create** &gt; **New Policy**
    2. Configure the following properties and select **Create**:

        - **Platform**: Select **Android Enterprise**.
        - **Profile type**: Select **Templates** &gt; **Fully Managed, Dedicated, and Corporate-Owned Work Profile** &gt; **Device restrictions**.
    3. Expand the **Applications** category and set the **Allow access to all apps in Google Play store** setting to **Allow**.
    4. Select **Next** and continue creating the profile. For step-by-step instructions, see [Create device profiles](../../device-configuration/create-device-profile).
2. Add the apps you want to block.

    When they're added to Intune, you can block the apps. Then they're considered managed apps.

    1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Create &gt; Managed Google Play app**.
    2. Select the AI app you want to block &gt; **Sync**.
    3. In **Apps &gt; Android &gt; Android apps**, make sure the app is shown in the list. The sync might take a few minutes.
3. Blocks specific apps by assigning them for **Uninstall**:

    If the apps are already installed on devices, assigning them for **Uninstall** removes them from the devices.

    1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Android apps**.
    2. Select the AI app you want to uninstall &gt; **Properties**.
    3. Select **Assignments** &gt; **Edit**.
    4. In **Uninstall**, add a group, users, or devices.

# [Personally owned devices](#tab/ai-apps-personal)
**Supported enrollment types**:

- Personally owned devices with a work profile (BYOD)

By default, no apps in the Google Play Store can be downloaded unless explicitly allowed. Use the following steps to make sure the app you want to block isn't already deployed to your devices.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Android apps**.
2. Select the AI app &gt; **Properties**.
3. Make sure **Assignments** is not set to **Required**, not set to **Available for enrolled devices**, or not set to **Available with or without enrollment**.

If all these options aren't set, then the app hasn't been deployed by an Intune policy.

It's possible the app was installed manually by the user or through another MDM solution. In this situation, set the assignment to **Uninstall** to remove it from the devices.

---

## Block AI Websites

![](../../media/icons/16/check.svg)**Goal - Block AI websites in web browser apps**

You can use Intune app configuration policies to block access to AI websites in web browser apps, like Microsoft Edge and Chrome. Only the websites you enter are blocked. So, you can also use this approach to only allow specific AI websites. If you use multiple browsers, you need to create a separate policy for each web browser app.

**Supported enrollment types**:

- Corporate owned fully managed devices (COBO)
- Corporate owned dedicated devices (COSU)
- Corporate owned devices with a work profile (COPE)
- Personally owned devices with a work profile (BYOD)

### Step 1 - Add your web browser as a managed app

To configure the browser settings, you first need to add the browser app to Intune so it becomes a managed app.

For the steps, see:

- It's possible the browser app is [built-in](../../app-management/deployment/add-built-in).
- If the app isn't built in, then you can [add your browser app from the Play Store](../../app-management/deployment/add-store-android).

### Step 2 - Create an app configuration policy

Use the following steps to create an app configuration policy that configures your web browser app to block access to the AI websites you enter.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Configuration &gt; Create &gt; Managed devices**.
2. In **Basics**, configure the following properties:

    - **Name**: Enter a name for the policy, like **Block AI Websites in Edge**.
    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select your enrollment type:

        - Fully Managed, Dedicated, and Corporate-Owned Work Profile Only
        - Personally Owned Work Profile devices
    - **Targeted app**: Select the browser app you added, like Microsoft Edge or Chrome.
3. Select **Next**.
4. In **Settings** &gt; **Configuration settings format**, select **Enter JSON data**. Enter the list of URLs to block. For example, enter:

    ```json
    {
      "key": "URLBlocklist",
      "valueStringArray": [ "https://chatgpt.com", "https://claude.ai", "https://copilot.microsoft.com", "https://perplexity.ai", "https://gemini.google.com" ]
    }
    ```
5. Select **Next** and continue creating the policy. For step-by-step instructions, see [Add App Configuration Policies for Managed Android Enterprise Devices](../../app-management/configuration/configure-managed-android).

## Block Screen-Driven AI Experiences

![](../../media/icons/16/check.svg)**Goal - Block features that can read on-screen content**

AI features can read on-screen content, and can provide insights & recommendations from screenshots and content displayed on the screen. Some of these features are built into the OS, like Circle to Search, and some are provided by assistant apps.

To block these features, you can use Intune to restrict screenshot abilities and block content sharing with privileged apps.

# [Fully managedDedicated](#tab/screen-fully-managed)
**Supported enrollment types**:

- Corporate owned fully managed devices (COBO)
- Corporate owned dedicated devices (COSU)

### Step 1 - Implement Basic Coverage

This step creates a settings catalog policy that configures the **Block assist content sharing with privileged apps** setting.

This setting blocks assist content, like screenshots and app details, from being sent to a privileged app, like an assistant app. The setting can be used on Android AI capabilities, like Circle to Search. This setting doesn't affect general screenshot abilities.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Create**.
4. In **Basics**, enter a **Name** for the profile, and select **Next**.
5. Select **Add settings**.
6. Select the **General** category &gt; **Block assist content sharing with privileged apps** setting. Set its value to **True**.
7. Select **Next** and continue creating the profile. For step-by-step instructions, see [Use the Intune settings catalog to configure settings](../../device-configuration/settings-catalog/).

### Step 2 - Implement Comprehensive Coverage (Optional)

For more comprehensive protection, you can also restrict screenshot abilities and other functionalities by blocking screen captures.

This setting blocks AI features from accessing on-screen content, but also disables screenshots device-wide.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Create**.
4. In **Basics**, enter a **Name** for the profile, and select **Next**.
5. Select **Add settings**.
6. Select the **General** category &gt; **Block Screen capture** setting. Set its value to **True**.

    This setting blocks AI features from accessing on-screen content. End users can't take screenshots on the device.
7. Select **Next** and continue creating the profile. For step-by-step instructions, see [Use the Intune settings catalog to configure settings](../../device-configuration/settings-catalog/).

# [Corporate owned with work profile](#tab/screen-corporate-owned)
**Supported enrollment types**:

- Corporate owned devices with a work profile (COPE)

### Step 1 - Implement Basic Coverage

This step creates a settings catalog policy that configures the **Block assist content sharing with privileged apps** setting.

This setting blocks assist content, like screenshots and app details, from being sent to a privileged app, like an assistant app. The setting can be used on Android AI capabilities, like Circle to Search. This setting doesn't affect general screenshot abilities.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Create**.
4. In **Basics**, enter a **Name** for the profile, and select **Next**.
5. Select **Add settings**.
6. Select the **General** category &gt; **Block assist content sharing with privileged apps** setting. Set its value to **True**.
7. Select **Next** and continue creating the profile. For step-by-step instructions, see [Use the Intune settings catalog to configure settings](../../device-configuration/settings-catalog/).

### Step 2 - Implement Comprehensive Coverage (Optional)

For more comprehensive protection, you can also restrict screenshot abilities and other functionalities using the following settings:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Next**.
4. In **Basics**, enter a **Name** for the profile, and select **Next**.
5. Select **Add settings**.
6. Select the **General** category and configure the following settings:

    - **Allow copy and paste between work and personal profiles**: Set to **False**. This setting blocks copy and paste functionality between work and personal profiles. This helps ensure that no data from the work profile leaks into AI apps in the personal profile.
    - **Block screen capture**: Set to **True**. This setting blocks AI features from accessing on-screen content. End users can't take screenshots in the work profile.
    - **Data sharing between work and personal profiles**: Set to **Block all sharing between profiles**. This setting blocks data sharing between work and personal profiles. It helps ensure that no data from the work profile leaks into AI apps in the personal profile.
7. Select the **Personal profile** category and configure the following setting:

    - **Block screen capture**: Set to **True**. This setting blocks AI features from accessing on-screen content. End users can't take screenshots in the personal profile.
8. Select **Next** and continue creating the profile. For step-by-step instructions, see [Use the Intune settings catalog to configure settings](../../device-configuration/settings-catalog/).
9. Create a device restrictions profile to block specific AI apps. This setting isn't available in the settings catalog. So, that's why you create a separate device restrictions profile.

    1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
    2. Enter the following properties:

        - **Platform**: Select **Android Enterprise**.
        - **Profile type**: Select **Templates** &gt; **Fully managed, dedicated, and Corporate-owned work profile** &gt; **Device restrictions**.
    3. Select **Create**.
    4. In **Basics**, enter a **Name** for the profile, and select **Next**.
    5. In **Configuration settings**, expand the **Personal profile** category and configure the following settings:

        - **Type of restricted apps list**: Set to **Blocked Apps** and add the AI apps you want to block.
    6. Select **Next** and continue creating the profile. For step-by-step instructions, see [Create device profiles](../../device-configuration/create-device-profile).

# [Personally owned with work profile](#tab/screen-personal)
**Supported enrollment types**:

- Personally owned devices with a work profile (BYOD)

To prevent sensitive data from being used by AI apps in the personal profile, you can configure the following settings. These settings help you manage data flow from the work profile to the personal profile.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Templates &gt; Personally-Owned work profile &gt; Device restrictions**.
3. Select **Create**.
4. In **Basics**, enter a **Name** for the profile, and select **Next**.
5. In **Configuration settings**, expand **Work profile settings** category. The following settings and their default values help limit AI data leakage. If any of these settings are changed from their default values, you should change them back to the defaults.

    - **Copy and paste between work and personal profiles**: Set to **Block** (default).
    - **Data sharing between work and personal profiles**: Set to **Device Default**. Device Default restricts sharing between work and personal profiles.
6. Select **Next** and continue creating the profile. For step-by-step instructions, see [Create device profiles](../../device-configuration/create-device-profile).

---

## Disable On-Device AI System App

![](../../media/icons/16/check.svg)**Goal - Block Google's local AI processing**

Gemini Nano is Google's on-device foundation model and processes AI interactions on the device. It enables AI summary and message reply capabilities in Messages, Recorder, GBoard, and other services. You can use Intune to disable the AICore system app.

**Supported enrollment types**:

- Corporate owned fully managed devices (COBO)
- Corporate owned dedicated devices (COSU)
- Corporate owned devices with a work profile (COPE)
- Personally owned devices with a work profile (BYOD)

Use the following steps to disable the AICore system app.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps &gt; Android &gt; Create**.
2. In **Select app type**, select **Other &gt; Android Enterprise system app**, and then choose **Select**.
3. In **App information**, configure the following properties, and then select **Next**:

    - **Name**: Enter `AICore`.
    - **Publisher**: Enter `Google Android`.
    - **Package Name**: Enter `com.google.android.aicore`.
4. In **Scope tags**, select **Next**.
5. In **Assignments &gt; Uninstall**, select the group assignments for the app. When you select **Uninstall**, the app is disabled.

    Select **Next**.
6. In **Review + create**, review the values and settings you entered for the app. When you're done, select **Create**.

## Disable OEM-Specific AI Capabilities

![](../../media/icons/16/check.svg)**Goal - Turn off OEM‑provided AI features**

OEMs can include their own AI features and capabilities on the device, like the Samsung Galaxy AI experiences through the Knox Service Plugin. These features are typically managed through the OEM's OEMConfig app. Using Intune, you can configure the OEMConfig app to manage these AI features.

To configure the OEMConfig app, you need to know the AI settings available in the app. Contact your OEMs to get a list of available AI controls in their OEMConfig apps.

For a list of supported OEMConfig apps, see [OEMConfig in Intune - Supported OEMConfig apps](../../device-configuration/templates/configure-oemconfig-android#supported-oemconfig-apps).

**Supported enrollment types**:

- Corporate owned fully managed devices (COBO)
- Corporate owned dedicated devices (COSU)
- Corporate owned devices with a work profile (COPE)
- Personally owned devices with a work profile (BYOD)

Use the following steps to add, deploy, and configure the OEMConfig app and its AI capabilities.

### Step 1 - Add the OEMConfig app

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Create &gt; Managed Google Play app &gt; Select**.
2. Select the OEMConfig app you want to configure.
3. Choose **Select** &gt; **Sync**.

Make sure the app is shown in the list (**Apps &gt; Android &gt; Android apps**). The sync can take a few minutes.

### Step 2 - Deploy the OEMConfig app

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Apps &gt; Android &gt; Android apps**.
2. Select the OEMConfig app you added.
3. Select **Properties** &gt; **Assignments** &gt; **Edit**.
4. Add your group and/or users to the following **Assignments**:

    - Required
    - Available for enrolled devices
    - Available with or without enrollment
5. Review and save your changes.

### Step 3 - Configure the OEMConfig app

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices &gt; Manage devices &gt; Configuration &gt; Create &gt; New policy**.
2. Enter the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Templates &gt; OEMConfig**.
3. Select **Create**.
4. In **Basics**, configure the following properties, and then select **Next**:

    - **Name**: Enter a name for the profile.
    - **OEMConfig app**: Select the OEMConfig app you added and assigned.
5. In **Configuration settings**, select **Configuration designer** or **JSON editor** to configure the settings available in the OEMConfig app. If you select **Configuration designer**, you might be able to use the **Locate** search box to find AI-related settings.

    The available settings depend on the OEMConfig app you select. Contact your OEM to get a list of available AI controls in their OEMConfig apps.
6. Select **Next** and continue creating the profile. For step-by-step instructions, see [Use and manage Android Enterprise devices with OEMConfig](../../device-configuration/templates/configure-oemconfig-android).

    Make sure you assign the profile to the same groups and/or users you assigned the OEMConfig app to.