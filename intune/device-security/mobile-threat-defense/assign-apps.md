---
layout: Conceptual
title: Add and assign MTD apps to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/assign-apps
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: Use Intune to add Mobile Threat Defense (MTD) apps, Microsoft Authenticator app, and iOS configuration policy in Microsoft Intune
ms.date: 2025-06-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 281236c8-1fe7-2f72-86f6-bbdbfba580ca
document_version_independent_id: 281236c8-1fe7-2f72-86f6-bbdbfba580ca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/assign-apps.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/assign-apps
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/assign-apps.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: eade2745-5645-0950-3f10-2fb5895d2edf
---

# Add and assign MTD apps to Microsoft Intune - Microsoft Intune | Microsoft Learn

You can use Intune to add and deploy Mobile Threat Defense (MTD) apps so that end users can receive notifications when a threat is identified in their mobile devices, and to receive guidance to remediate the threats.

Note

This article applies to all Mobile Threat Defense partners.

## Before you begin

Complete the following steps in Intune. Make sure you're familiar with the process of:

- [Adding an app into Intune](../../app-management/deployment/).
- [Adding an iOS app configuration policy into Intune](../../app-management/configuration/configure-managed-ios).
- [Assigning an app with Intune](../../app-management/deployment/assign-groups).

Tip

The Intune Company Portal works as the broker on Android devices so users can have their identities checked by Microsoft Entra.

## Configure Microsoft Authenticator for iOS

For iOS devices, you need the [Microsoft Authenticator](https://support.microsoft.com/account-billing/download-microsoft-authenticator-351498fc-850a-45da-b7b6-27e523b8702a) so users can have their identities checked by Microsoft Entra ID. Additionally, you need an iOS app configuration policy that sets the MTD iOS app you use with Intune.

See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Microsoft Authenticator app store URL](https://apps.apple.com/us/app/microsoft-authenticator/id983156458) when you configure **App information**.

## Configure your MTD apps with an app configuration policy

To simplify user onboarding, the Mobile Threat Defense apps on MDM-managed devices use app configuration. For unenrolled devices, MDM based app configuration isn't available. See [Add Mobile Threat Defense apps to unenrolled devices](add-apps-unenrolled-devices).

### BlackBerry Protect configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the BlackBerry Protect iOS app configuration policy.

### Better Mobile app configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Better Mobile iOS app configuration policy.

- For **Configuration settings format**, select **Enter XML data**, copy the following content and paste it into the configuration policy body. Replace the `https://client.bmobi.net` URL with the appropriate console URL.

    ```
    <dict>
    <key>better_server_url</key>
    <string>https://client.bmobi.net</string>
    <key>better_udid</key>
    <string>{{aaddeviceid}}</string>
    <key>better_user</key>
    <string>{{userprincipalname}}</string>
    </dict>
    ```

### Check Point Harmony Mobile Protect app configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Check Point Harmony Mobile iOS app configuration policy.

- For **Configuration settings format**, select **Enter XML data**, copy the following content and paste it into the configuration policy body.

    `<dict><key>MDM</key><string>INTUNE</string></dict>`

### CrowdStrike Falcon for Mobile app configuration policy

To configure **Android Enterprise** and **iOS** app configuration policies for CrowdStrike Falcon, see [Integrating Falcon for Mobile with Microsoft Intune for remediation actions](https://falcon.crowdstrike.com/documentation/page/odf8977b/integrating-falcon-for-mobile-with-microsoft-intune-for-remediation-actions) in the CrowdStrike documentation. You must sign in with your CrowdStrike credentials before you can access this content.

For general guidance about Intune app configuration policies, see the following articles in the Intune documentation:

- [Android managed devices](../../app-management/configuration/configure-managed-android)
- [iOS managed devices](../../app-management/configuration/configure-managed-ios)

### Jamf Trust app configuration policy

Note

For initial testing, use a test group when assigning users and devices in the Assignments section of the configuration policy.

- **Android Enterprise**: See the instructions for [using Microsoft Intune app configuration policies for Android](../../app-management/configuration/configure-managed-android) to add the Jamf Android app configuration policy using the following information when prompted.

    1. In the **Jamf Portal**, select the **Add** button under **Configuration settings** format.
    2. Select **Activation Profile URL** from the list of **Configuration Keys**. Select **OK**.
    3. For **Activation Profile URL** select **string** from the **Value type** menu then copy the **Shareable Link URL** from the desired Activation Profile in Jamf Security Cloud.
    4. In the **Intune admin center app configuration UI**, select **Settings**, define **Configuration settings format &gt; Use Configuration Designer** and paste the **Shareable Link URL**.

    Note

    Unlike iOS, you'll need to define a unique Android Enterprise app configuration policy for each Activation Profile. If you don't require multiple Activation Profiles, you can use a single Android app configuration for all target devices. When creating Activation Profiles in Jamf, be sure to select Microsoft Entra ID under the Associated User configuration to ensure Jamf is able to synchronize the device with Intune via UEM Connect.
- **iOS**: See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Jamf iOS app configuration policy using the following information when prompted.

    1. In **Jamf Security Cloud**, navigate to **Devices &gt; Activation profiles** and select any activation profile. Select **Deployment Strategies &gt; Managed Devices &gt; Microsoft Intune** and locate the **iOS App Configuration settings**.
    2. Expand the box to reveal the iOS app configuration XML and copy it to your system clipboard.
    3. In **Intune admin center app configuration UI Settings,** define **Configuration settings format &gt; Enter XML data**.
    4. Paste the XML in the app configuration text box.

    Note

    A single iOS configuration policy can be used across all devices that are to be provisioned with Jamf.

### Lookout for Work app configuration policy

Create the iOS app configuration policy as described in the [using iOS app configuration policy](../../app-management/configuration/configure-managed-ios) article.

### Pradeo app configuration policy

Pradeo doesn't support application configuration policy on iOS/iPadOS. Instead, to get a configured app, work with Pradeo to implement custom IPA or APK files that are preconfigured with the settings you want.

### SentinelOne app configuration policy

- **Android Enterprise**:

    See the instructions for [using Microsoft Intune app configuration policies for Android](../../app-management/configuration/configure-managed-android) to add the SentinelOne Android app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:
- **iOS**:

    See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the SentinelOne iOS app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:

    | Configuration key | Value type | Configuration value |
    | --- | --- | --- |
    | MDMDeviceID | string | `{{AzureADDeviceId}}` |
    | tenantid | string | Copy value from admin console *Manage* page in the SentinelOne console |
    | defaultchannel | string | Copy value from admin console *Manage* page in the SentinelOne console |

### SEP Mobile app configuration policy

Use the same Microsoft Entra account previously configured in the [Symantec Endpoint Protection Management console](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/logging-on-to-the-console-v8025272-d23e2462.html), which should be the same account used to sign in to the Intune.

- **Download** the iOS app configuration policy file:

    - Go to [Symantec Endpoint Protection Management console](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/logging-on-to-the-console-v8025272-d23e2462.html) and sign in with your admin credentials.
    - Go to **Settings**, and under **Integrations**, choose **Intune**. Choose **EMM Integration Selection**. Choose **Microsoft**, and then save your selection.
    - Select the **Integration setup files** link and save the generated \*.zip file. The .zip file contains the \***.plist** file that is used to create the iOS app configuration policy in Intune.
    - See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the SEP Mobile iOS app configuration policy.

        - For **Configuration settings format**, select **Enter XML data**, copy the content from the \***.plist** file, and paste its content into the configuration policy body.

    Note

    If you're unable to retrieve the files, contact [Symantec Endpoint Protection Mobile Enterprise Support](https://support.symantec.com/en_US/contact-support.html).

### Sophos Mobile app configuration policy

Create the iOS app configuration policy as described in the [using iOS app configuration policy](../../app-management/configuration/configure-managed-ios) article.

### Trellix Mobile Security app configuration policy

- **Android Enterprise**: See the instructions for [using Microsoft Intune app configuration policies for Android](../../app-management/configuration/configure-managed-android) to add the Trellix Mobile Security Android app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:

    | Configuration key | Value type | Configuration value |
    | --- | --- | --- |
    | MDMDeviceID | string | `{{AzureADDeviceId}}` |
    | tenantid | string | Copy value from admin console *Manage* page in the Trellix console |
    | defaultchannel | string | Copy value from admin console *Manage* page in the Trellix console |
- **iOS**: See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Trellix Mobile Security iOS app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:

    | Configuration key | Value type | Configuration value |
    | --- | --- | --- |
    | MDMDeviceID | string | `{{AzureADDeviceId}}` |
    | tenantid | string | Copy value from admin console *Manage* page in the Trellix console |
    | defaultchannel | string | Copy value from admin console *Manage* page in the Trellix console |

### Trend Micro Mobile Security as a Service app configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Trend Micro Mobile Security as a Service app configuration policy.

### Trustd Mobile app configuration policy

See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Trustd Mobile iOS app configuration policy.

### Zimperium app configuration policy

- **Android Enterprise**:

    See the instructions for [using Microsoft Intune app configuration policies for Android](../../app-management/configuration/configure-managed-android) to add the Zimperium Android app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:

    | Configuration key | Value type | Configuration value |
    | --- | --- | --- |
    | MDMDeviceID | string | `{{AzureADDeviceId}}` |
    | tenantid | string | Copy value from admin console *Manage* page in the Zimperium console |
    | defaultchannel | string | Copy value from admin console *Manage* page in the Zimperium console |
- **iOS**: See the instructions for [using Microsoft Intune app configuration policies for iOS](../../app-management/configuration/configure-managed-ios) to add the Zimperium iOS app configuration policy.

    For **Configuration settings format**, select **Use configuration designer**, and add the following settings:

    | Configuration key | Value type | Configuration value |
    | --- | --- | --- |
    | MDMDeviceID | string | `{{AzureADDeviceId}}` |
    | tenantid | string | Copy value from admin console *Manage* page in the Zimperium console |
    | defaultchannel | string | Copy value from admin console *Manage* page in the Zimperium console |

## Assigning Mobile Threat Defense apps to end users via Intune

To install the Mobile Threat Defense app on the end user device, you can follow the steps that are detailed in the following sections. Make sure you're familiar with the process of:

- [Assigning apps to groups with Intune](../../app-management/deployment/assign-groups)

Choose the section that corresponds to your MTD provider:

- Better Mobile
- Check Point Harmony Mobile Protect
- CrowdStrike Falcon for Mobile
- Jamf
- Lookout for Work
- Pradeo
- SentinelOne
- Sophos Mobile
- Symantec Endpoint Protection Mobile (SEP Mobile)
- Trellix Mobile Security
- Trustd Mobile
- Zimperium

### Assigning Better Mobile

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android).
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [ActiveShield app store URL](https://itunes.apple.com/us/app/activeshield/id980234260) for the **Appstore URL**.

### Assigning Check Point Harmony Mobile Protect

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Check Point Harmony Mobile Protect app store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Check Point Harmony Mobile Protect app store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) for the **Appstore URL**.

### Assigning CrowdStrike Falcon for Mobile

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android).
    - Use the URL for [CrowdStrike Falcon](https://play.google.com/store/apps/details?id=com.crowdstrike.falconmobile) from the app store for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios).
    - Use the URL for [CrowdStrike Falcon](https://apps.apple.com/us/app/crowdstrike-falcon/id1458815656) from the app store for the **Appstore URL**.

### Assigning Jamf

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Jamf Mobile app store URL](https://play.google.com/store/apps/details/?id=com.wandera.android) for the **Appstore URL**. For **Minimum operating system**, select **Android 11**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Jamf Mobile app store URL](https://apps.apple.com/us/app/jamf-trust/id1608041266?mt=8) for the **Appstore URL**.

### Assigning Lookout for Work

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Lookout for work Google app store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Lookout for Work iOS app store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468) for the **Appstore URL**.
- **Lookout for Work app outside the Apple store**:

    - You must re-sign the Lookout for Work iOS app. Lookout distributes its Lookout for Work iOS app outside of the iOS App Store. Before distributing the app, you must re-sign the app with your iOS Enterprise Developer Certificate. Contact Lookout for Work for detailed instructions on this process.
    - **Enable Microsoft Entra authentication for Lookout for Work iOS app users.**

        1. Go to the [Azure portal](https://portal.azure.com), sign in with your credentials, then navigate to the application page.
        2. Add the **Lookout for Work iOS app** as a **native client application**.
        3. Replace the **com.lookout.enterprise.yourcompanyname** with the customer bundle ID you selected when you signed the IPA.
        4. Add another redirect URI: **&lt;companyportal://code/&gt;** followed by a URL encoded version of your original redirect URI.
        5. Add **Delegated Permissions** to your app.

        Note

        See [Configure your App Service or Azure Functions app to use Microsoft Entra sign-in](/en-us/azure/app-service/configure-authentication-provider-aad?tabs=workforce-configuration#-configure-client-apps-to-access-app-service) for more details.
    - **Add the Lookout for Work ipa file.**

        - Upload the re-signed .ipa file as described in the [Add iOS LOB apps with Intune](../../app-management/deployment/add-lob-ios) article. You also need to set the minimum OS version to iOS 8.0 or later.

### Assigning Pradeo

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Pradeo app store URL](https://play.google.com/store/apps/details?id=net.pradeo.service) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Pradeo app store URL](https://apps.apple.com/us/app/pradeo-security/id6743930611) for the **Appstore URL**.

### Assigning SentinelOne

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [SentinalOne app store URL](https://play.google.com/store/apps/details?id=com.sentinelone.mobile) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [SentinalOne app store URL](https://apps.apple.com/us/app/sentinelone-mobile/id1567458126) for the **Appstore URL**.

### Assigning Sophos

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Sophos app store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [ActiveShield app store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662) for the **Appstore URL**.

### Assigning Symantec Endpoint Protection Mobile

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) for the **Appstore URL**. For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [SEP Mobile app store URL](https://itunes.apple.com/us/app/skycure/id695620821) for the **Appstore URL**.

### Assigning Trellix Mobile Security

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Trellix Mobile Security app store URL](https://play.google.com/store/apps/details?id=com.mcafee.mvision) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Trellix Mobile Security app store URL](https://apps.apple.com/us/app/mcafee-mvision-mobile/id1435156022) for the **Appstore URL**.

### Assigning Trustd Mobile

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Trustd Mobile app store URL](https://play.google.com/store/apps/details?id=app.traced) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Trustd Mobile app store URL](https://apps.apple.com/app/trustd-mobile-security/id1519403888) for the **Appstore URL**.

### Assigning Zimperium

- **Android**:

    - See the instructions for [adding Android store apps to Microsoft Intune](../../app-management/deployment/add-store-android). Use this [Zimperium app store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips) for the **Appstore URL**.
- **iOS**:

    - See the instructions for [adding iOS store apps to Microsoft Intune](../../app-management/deployment/add-store-ios). Use this [Zimperium app store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459) for the **Appstore URL**.