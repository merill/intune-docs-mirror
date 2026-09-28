---
layout: Conceptual
title: Microsoft Intune App SDK for iOS Developer Guide - MSAL Prerequisite and Setup - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/app-sdk/ios-phase-2
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- iOS/iPadOS
ms.reviewer: jamiesil
ms.subservice: developer
description: The Microsoft Intune App SDK for iOS lets you incorporate Intune app protection policies (also known as MAM policies) into your native iOS app. MSAL prerequisite and setup
ms.date: 2025-06-12T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: d251b9cb-4bdd-5e34-7df6-57478eae94b6
document_version_independent_id: d251b9cb-4bdd-5e34-7df6-57478eae94b6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/app-sdk/ios-phase-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/app-sdk/ios-phase-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/app-sdk/ios-phase-2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5f286262-a4cb-47f4-92d3-dc24f172492b
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e31b9be-b6e9-4221-a20b-d1460dbd5dfa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90571f66-8410-4272-8117-79ce87fc2dcc
- https://authoring-docs-microsoft.poolparty.biz/devrel/8d63a4c4-4889-43b4-a98e-8e50dbfdb083
platformId: d1a5f17a-191d-3e2c-a761-cec606006e6f
---

# Microsoft Intune App SDK for iOS Developer Guide - MSAL Prerequisite and Setup - Microsoft Intune | Microsoft Learn

The Intune App SDK uses the [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-objc) for its authentication and conditional launch scenarios. It also relies on MSAL to register the user identity with the MAM service for management without device enrollment scenarios.

Note

This guide is divided into several distinct stages. Start by reviewing [Stage 1: Planning the Integration](ios-phase-1).

## Stage Goals

- Register your application with Microsoft Entra ID.
- Integrate MSAL into your iOS application.
- Verify that your application can obtain a token that grants access to protected resources.

### Set up and configure a Microsoft Entra app registration

MSAL requires apps to [register](/en-us/azure/active-directory/develop/quickstart-register-app) with Microsoft Entra ID and create a unique client ID and redirect URI, to guarantee the security of the tokens granted to the app. If your application already uses MSAL for its own authentication, then there should already be a Microsoft Entra app registration/client ID/redirect URI associated with the app.

If your app doesn't already use MSAL, you'll need to configure an app registration in Microsoft Entra ID and specify the client ID and redirect URI that the Intune SDK should use.

If your app currently uses ADAL to authenticate users, see [Migrate applications to MSAL for iOS and macOS](/en-us/azure/active-directory/develop/migrate-objc-adal-msal) for more information on migrating your app from ADAL to MSAL.

It's recommended that your app links to the latest release of [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases).

### Link MSAL to Your Project

Follow the [installation](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation) section to put the MSAL binaries in your app.

### Configure MSAL

Follow the [configuration](https://github.com/AzureAD/microsoft-authentication-library-for-objc#configuring-msal) section to configure MSAL. Make sure you follow all the steps in the configuration section. Disregard step one if your app is already registered in Microsoft Entra ID.

The points below contain additional information to configure MSAL and link to it. Follow these if they apply to your application.

- If your app doesn't have any keychain access groups defined, add the app's bundle ID as the first group.
- Enable MSAL single sign-on (SSO) by adding `com.microsoft.adalcache` to the keychain access groups.
- In the case you're explicitly setting the MSAL shared cache keychain group, make sure it's set to `<appidprefix>.com.microsoft.adalcache`. MSAL will set this for you unless you override it. If you want to specify a custom keychain group to replace `com.microsoft.adalcache`, specify that in the Info.plist file under IntuneMAMSettings, by using the key `ADALCacheKeychainGroupOverride`.

### Configure MSAL settings for the Intune App SDK

Once an app registration has been configured for your application in Microsoft Entra ID, you can configure the Intune App SDK to use the settings from your app registration during authentication against Microsoft Entra ID. See Configure settings for the Intune App SDK for information on populating the following settings:

- ADALClientId
- ADALAuthority
- ADALRedirectUri
- ADALRedirectScheme
- ADALCacheKeychainGroupOverride

The following configurations are required:

1. In the project's Info.plist file, under the **IntuneMAMSettings** dictionary with the key name `ADALClientId`, specify the client ID to be used for MSAL calls.
2. If the Microsoft Entra app registration which maps to the client ID configured in step 1 is configured for use in only a single Microsoft Entra tenant, configure the `ADALAuthority` key under the **IntuneMAMSettings** dictionary within the application's Info.plist file. Specify the Microsoft Entra authority to be used by MSAL for acquiring tokens for the Intune mobile application management service.
3. Also under the **IntuneMAMSettings** dictionary with the key name `ADALRedirectUri`, specify the redirect URI to be used for MSAL calls. Alternatively, you could specify `ADALRedirectScheme` instead, if the application's redirect URI is in the format `scheme://bundle_id`.

    Alternatively, apps can override these Microsoft Entra settings at runtime. To do this, simply set the `aadAuthorityUriOverride`, `aadClientIdOverride`, and `aadRedirectUriOverride` properties on the `IntuneMAMSettings` class.
4. Ensure the steps to give your iOS app permissions to the Intune Mobile App Management (MAM) service are followed. Use the instructions in the [getting started with the Intune SDK guide](quickstart-integration#next-steps-after-integration) under [Give your app access to the Intune Mobile App Management service](quickstart-integration#give-your-app-access-to-the-intune-mobile-app-management-service).

    Note

    If the app protection policy is related to managed devices, creating an app configuration profile of the application that has Intune integrated is also necessary.

    The Info.plist approach is recommended for all settings which are static and do not need to be determined at runtime. Values assigned to the `IntuneMAMSettings` class properties at runtime take precedence over any corresponding values specified in the Info.plist, and will persist even after the app is restarted. The SDK will continue to use them for policy check-ins until the user is unenrolled or the values are cleared or changed.

### Special considerations when using MSAL for app-initiated authentication

It's recommended that applications don't use SFSafariViewController, SFAuththenticationSession or ASWebAuthenticationSession as their webview for any app-initiated MSAL interactive auth operations. By default, MSAL uses ASWebAuthenticationSession, so app developers should [explicitly set the webview type](/en-us/azure/active-directory/develop/customize-webviews#change-the-default-browser-for-the-request) to WKWebView. If for some reason your app must use a webview type other than WKWebView for any interactive MSAL auth operations, then it must also set `SafariViewControllerBlockedOverride` to `true` under the `IntuneMAMSettings` dictionary in the application's Info.plist.

Warning

This will turn off Intune's SafariViewController hooks to enable the auth session. This does risk data leaks elsewhere in the app if the application uses SafariViewController to view corporate data, so the application shouldn't show corporate data in any of those webview types.

## Exit Criteria

- Have you registered your app on the Microsoft Entra app registration page?
- Have you integrated MSAL into your application?
- Have you enabled broker authentication by generating a redirect URI and setting it in the MSAL configuration file?
- Have you made sure the required configuration information for MSAL in your IntuneMAMSettings dictionary matched the ones in your Microsoft Entra App Registrations?

## FAQ

### What about ADAL?

Microsoft's previous authentication library, [Azure Active Directory Authentication Library (ADAL)](/en-us/azure/active-directory/azuread-dev/active-directory-authentication-libraries), is **deprecated**.

If your application has already integrated ADAL, see [Update your applications to use Microsoft Authentication Library (MSAL)](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/update-your-applications-to-use-microsoft-authentication-library/ba-p/1257363). To migrate your app from ADAL to MSAL, see [Migrate applications to MSAL for iOS and macOS](/en-us/azure/active-directory/develop/migrate-objc-adal-msal)

**It is recommended to migrate from ADAL to MSAL prior to integrating the Intune App SDK.**