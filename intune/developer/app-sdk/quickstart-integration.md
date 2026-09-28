---
layout: Conceptual
title: Get Started With the Microsoft Intune App SDK - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/app-sdk/quickstart-integration
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.reviewer: jamiesil
ms.subservice: developer
description: Quickly enable your mobile app for mobile application management (MAM) with Microsoft Intune.
ms.date: 2025-04-01T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: c3c143b7-9750-0292-3a99-2f502c0ceea7
document_version_independent_id: c3c143b7-9750-0292-3a99-2f502c0ceea7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/app-sdk/quickstart-integration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/app-sdk/quickstart-integration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/app-sdk/quickstart-integration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/f0c462af-0ef9-4821-b36f-ba3d94736e2b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/1209ac18-fe8e-4ac6-b056-073f0e2c78ab
platformId: 036e588e-2101-89b1-f61d-2b4beed33eb2
---

# Get Started With the Microsoft Intune App SDK - Microsoft Intune | Microsoft Learn

Important

Xamarin support has ended as of May 1, 2024 for all Xamarin SDKs including Xamarin.Forms, Intune App SDK Xamarin Bindings, and related Microsoft Tunnel support. Xamarin.Forms has evolved into .NET Multi-platform App UI (MAUI). Existing Xamarin projects should be migrated to .NET MAUI. For more information about upgrading Xamarin projects to .NET, see the [Upgrade from Xamarin to .NET & .NET MAUI](/en-us/dotnet/maui/migration/?WT.mc_id=dotnet-35129-website) and [.NET Multi-platform App UI](/en-us/dotnet/maui) documentation. For Intune support on the Android platform, see [Intune App SDK for .NET MAUI - Android](https://www.nuget.org/packages/Microsoft.Intune.Maui.Essentials.android) and [.NET for Android documentation](/en-us/dotnet/android/). For Intune support on the iOS platform, see [Microsoft Intune App SDK for MAUI.iOS](https://www.nuget.org/packages/Microsoft.Intune.Maui.Essentials.iOS) and [.NET for iOS](/en-us/dotnet/ios/).

This guide will help you quickly enable your mobile app to support app protection policies with Microsoft Intune. You may find it useful to first understand the benefits of the Intune App SDK, as explained in the [Intune App SDK overview](./).

The Intune App SDK supports similar scenarios across iOS and Android, and is intended to create a consistent experience across the platforms for IT admins. But there are small differences in the support of certain features, because of platform differences and limitations.

## Process flow

The following diagram provides the process flow for the Intune App SDK for iOS and the Intune App SDK for Android:

[![High-level architectural diagram for Microsoft Intune.](media/quickstart-integration/intune-app-sdk-combined-process-flow.svg)](media/quickstart-integration/intune-app-sdk-combined-process-flow.png#lightbox)

## Register your store app with Microsoft

### If your app is internal to your organization and won't be publicly available:

You ***do not need*** to register your app. For internal [line-of-business (LOB) apps](../../app-management/deployment/#app-types-in-microsoft-intune) that were written by or for your company, the IT administrator will deploy the app internally. Intune will detect that the app has been built with the SDK, and will let the IT administrator apply app protection policies to it. You can skip to the section Enable your iOS or Android app for app protection policy.

### If your app will be released to a public app store, like the Apple App Store or Google Play:

You ***must*** first register your app with Microsoft Intune and agree to the registration terms. IT administrators can then apply an app protection policy to the managed app, which will be listed as an [Partner productivity apps](../../app-management/ref-protected-apps#partner-productivity-apps).

Until registration has been finished and confirmed by the Microsoft Intune team, Intune administrators won't have the option to apply app protection policy to your app's deep link. Microsoft will also add your app to its Microsoft Intune Partners page. There, the app's icon will be displayed to show that it supports Intune app protection policies.

### The registration process

Once you have completed the Intune integration and successfully tested your app, and you would like your app to be listed as in [Partner productivity apps](../../app-management/ref-protected-apps#partner-productivity-apps), complete the [Microsoft Intune App Partner Questionnaire](https://aka.ms/IntuneAppPartner).

Please provide complete and accurate information in all required fields. If required information is missing or inaccurate, we won't be able to proceed with the next steps to add your app.

We will use the email addresses provided in the questionnaire to contact you if we need additional information to process your submission.

Note

All information collected in the questionnaire and through email correspondence with the Microsoft Intune team will honor the [Microsoft Privacy Statement](https://www.microsoft.com/privacystatement/default.aspx).

**What to expect in the registration process**:

1. We'll review the information provided in your submission. If additional information is required, we'll contact you using the email address provided in the questionnaire.
2. Once we have all required information, we'll send you the Microsoft Intune App Partner Agreement to sign. This agreement describes the terms your company must accept before becoming a Microsoft Intune app partner.
3. After the required steps are completed, your app will be added to the Microsoft Intune supported apps list. The listing process can take up to 2–3 months after we receive your completed submission.
4. While your app is awaiting listing, administrators can manually target the app using its bundle ID or package ID.

The deep link is the link to your app's listing in the public app store. If your app's deep link changes in the future, you'll need to re-register your app.

## Download the SDK files

The Intune App SDKs for native iOS and Android are hosted on a Microsoft GitHub account. These public repositories have the SDK files for native iOS and Android, respectively:

- [Intune App SDK for iOS](https://github.com/microsoftconnect/ms-intune-app-sdk-ios)
- [Intune App SDK for Android](https://github.com/microsoftconnect/ms-intune-app-sdk-android)

If your app builds with [.NET Multi-platform App UI (.NET MAUI)](https://dotnet.microsoft.com/en-us/apps/maui), use this SDK variant:

- [Intune App SDK for .NET MAUI - Android](https://www.nuget.org/packages/Microsoft.Intune.Maui.Essentials.android)
- [Intune App SDK for .NET MAUI - iOS](https://www.nuget.org/packages/Microsoft.Intune.Maui.Essentials.iOS)

Note

Using the Intune APP SDK for .NET MAUI, you can develop Android or iOS apps for Intune that incorporate the [.NET Multi-platform App UI](https://dotnet.microsoft.com/apps/maui). Apps developed using this framework will allow you to enforce [Intune mobile application management](../../app-management/overview).

It's a good idea to sign up for a GitHub account that you can use to fork and pull from our repositories. GitHub lets developers communicate with our product team, open issues and receive quick responses, view release notes, and provide feedback to Microsoft. For questions on the Intune App SDK GitHub, contact msintuneappsdk@microsoft.com.

## Enable your iOS or Android app for app protection policy

You'll need one of the following developer guides to help you integrate the Intune App SDK into your app:

- **[Intune App SDK for iOS Developer Guide](ios-phase-1)**: This document will walk you step-by-step through enabling your native iOS app with the Intune App SDK.
- **[Intune App SDK for Android Developer Guide](android-phase-1)**: This document will walk you step-by-step through enabling your native Android app with the Intune App SDK.

Important

Intune regularly releases updates to the [Intune App SDK](https://github.com/msintuneappsdk). We recommend subscribing to the [Intune App SDK](https://github.com/msintuneappsdk) repositories for updates so that you can incorporate the update into your software development release cycle and ensure your apps support the latest App Protection Policy settings.

Plan to take mandatory Intune App SDK updates prior to every major OS release to ensure your app continues to run smoothly as OS updates can cause breaking changes. If you do not update to the latest version prior to a major OS release, you may run the risk of encountering a breaking change and/or being unable to apply app protection policies to your app.

## Enable your iOS or Android app for app based Conditional Access

In addition to enabling your app for app protection policy, the following is required for your app to properly function with Microsoft Entra app based Conditional Access:

- App is built with the [Microsoft Authentication Library](/en-us/azure/active-directory/develop/reference-v2-libraries) and enabled for Microsoft Entra broker authentication.
- The [Microsoft Entra Client ID](/en-us/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#configure-a-native-client-application) for your app must be unique across iOS and Android platforms.

## Configure Telemetry for your app

Microsoft Intune collects data on usage statistics for your app.

- **Intune App SDK for iOS**: The SDK logs SDK telemetry data on usage events by default. This data is sent to Microsoft Intune.

    - If you choose not to send SDK telemetry data to Microsoft Intune from your app, you must disable telemetry transmission by setting the property `MAMTelemetryDisabled` to "YES" in the IntuneMAMSettings dictionary.
- **Intune App SDK for Android**: The Intune App SDK for Android doesn't control data collection from your app. The Company Portal application logs telemetry data by default. This data is sent to Microsoft Intune. As per Microsoft Policy, we don't collect any personally identifiable information (PII).

    - If end users choose not to send this data, they must turn off telemetry under Settings on the Company Portal app. To learn more, see [Turn off Microsoft usage data collection](../../user-help/privacy/disable-usage-data-collection-android).

## Line-of-business app version numbers

Line-of-business apps in Intune now display the version number for iOS and Android apps. The number displays in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) in the app list and in the app overview blade. End users can see the app number in the Company Portal app and in the web portal.

### Full version number

The full version number identifies a specific release of the app. The number appears as *Version*(*Build*). For example, 2.2(2.2.17560800).

The full version number has two components:

- **Version** The version number is the human-readable release number of the app. This is used by end users to identify different releases of the app.
- **Build Number** The build number is an internal number that can be used in app detection and to programmatically manage the app. The build number refers to an iteration of the app that references changes in the code.

### Version and build number in Android and iOS

Android and iOS both use version and build numbers in reference to apps. However, both operating systems have meanings that are OS-specific. The following table explains how these terms are related.

When you're developing a line-of-business application for use in Intune, remember to use both the version, and the build number. Intune App management features rely on a meaningful **CFBundleVersion** (for iOS) and **PackageVersionCode** (for Android). These numbers are included in the app manifest.

| Intune | iOS | Android | Description |
| --- | --- | --- | --- |
| Version number | CFBundleShortVersionString | PackageVersionName | This number indicates a specific release of the app for end users. |
| Build number | CFBundleVersion | PackageVersionCode | This number is used to indicate an iteration in the app code. |

#### iOS

- **CFBundleShortVersionString** Specifies the release version number of the bundle. This number identifies a released version of the app. The number is used by end users to reference the app.
- **CFBundleVersion** The build version of the bundle, which identifies an iteration of the bundle. The number may identify a release or unreleased bundle. The number is used for app detection.

#### Android

- **PackageVersionName** The version number shown to users. This attribute can be set as a raw string or as a reference to a string resource. The string has no other purpose than to be displayed to users.
- **PackageVersionCode** An internal version number. This number is used only to determine whether one version is more recent than another, with higher numbers indicating more recent versions. This isn't the version

## Next steps after integration

### Test your app

After you finish the necessary steps to integrate your iOS or Android app with the Intune App SDK, you'll need to ensure that all the app protection policies are enabled and functioning for the user and the IT admin. To test your integrated app, you'll need the following:

- **Microsoft Intune test account**: To test your Intune-managed app against Intune app protection features, you'll need a Microsoft Intune account.

    - If you're an ISV enabling your iOS or Android store apps for Intune app protection policy, you'll receive a promo code after you finish the registration with Microsoft Intune, as outlined in the registration step. The promo code will let you sign up for a Microsoft Intune trial for one year of extended use.
    - If you're developing a line-of-business app that won't be shipped to the store, you're expected to have access to Microsoft Intune through your organization. You can also sign up for a one-month free trial in [Microsoft Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&amp;dl=INTUNE_A&amp;ali=1#0).
    - If you're testing your app on a mobile device using an end user account, ensure that you have given that account an Intune license by in the Microsoft 365 admin center website after logging in with an admin account, see [Assign Microsoft Intune license](../../fundamentals/assign-licenses).
- **Intune app protection policies**: To test your app against all the Intune app protection policies, you should know what the expected behavior is for each policy setting. See the descriptions for [iOS app protection policies](../../app-management/protection/ref-settings-ios) and [Android app protection policies](../../app-management/protection/ref-settings-android). If your app has integrated the Intune SDK, but isn't listed in the list of targetable apps, you can specify the app's bundle ID (iOS) or package name (Android) in the text box when selecting **Custom Apps**.
- **Troubleshoot**: If you run into any issues while manually testing your app's installation user experience, see [Troubleshoot app installation issues](/en-us/troubleshoot/mem/intune/troubleshoot-app-install).

### Give your app access to the Intune Mobile App Management service

If your app is using its own custom Microsoft Entra settings for authentication, then the following steps should be taken for both public store apps, as well as internal LOB apps. The steps **do not need to be taken if your app is using the Intune SDK default client ID**.

Once you have registered your app within an Azure tenant, and it's showing up under **All Applications**, you must give your app access to the Intune Mobile App Management service. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431):

1. Go to the **Microsoft Entra ID** blade.
2. Under **App registrations**, go to the listing set up for the application.
3. Click **+ Add a permission**.
4. Click on the **APIs my organization uses**.
5. In the search box, enter **Microsoft Mobile Application Management**.
6. Under **Delegated Permissions**, select the **DeviceManagementManagedApps.ReadWrite: Read and Write the User's App Management Data**\* checkbox.
7. Click **Add permissions**.

### Badge your app (optional)

After validating that Intune app protection policies work in your app, you can badge your app icon with the Intune app protection logo.

This badge indicates to IT administrators, end-users, and potential Intune customers that your app works with Intune app protection policies. It encourages the usage and adoption of your app by Intune customers.

The badge is a briefcase icon and can be seen in the samples below:

![Intune app protection policies - Badge example 1](media/quickstart-integration/badge-example-1.png)![Intune app protection policies - Badge example 2](media/quickstart-integration/badge-example-2.png)

**What you'll need to badge your app**:

- An image manipulation application that can read **.eps** files, or an Adobe application that can read **.ai** files.
- You can find the [Intune app badge assets and guidelines](https://github.com/msintuneappsdk/intune-app-partner-badge) on the Microsoft Intune GitHub.