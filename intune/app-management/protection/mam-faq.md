---
layout: FAQ
title: Frequently asked questions about MAM and app protection - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/mam-faq
summary: >
  <p>This article provides answers to some frequently asked questions on Intune mobile application management (MAM) and Intune app protection.</p>
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.subservice: apps
description: This article provides answers to some frequently asked questions on Intune mobile application management (MAM) and Intune app protection.
ms.date: 2025-06-05T00:00:00.0000000Z
ms.topic: faq
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 9bb15dc9-7a15-5ae6-296b-2de864e4fdee
document_version_independent_id: 9bb15dc9-7a15-5ae6-296b-2de864e4fdee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/mam-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/mam-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/mam-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 6027ca34-391a-922c-549c-3e55271ab4a9
---

# Frequently asked questions about MAM and app protection - Microsoft Intune | Microsoft Learn

This article provides answers to some frequently asked questions on Intune mobile application management (MAM) and Intune app protection.

## MAM Basics

### What is MAM?

[MAM Overview](../overview#mobile-application-management-mam-basics)

## App protection policies

### What are app protection policies?

App protection policies are rules that ensure an organization's data remains safe or contained in a managed app. A policy is a rule that Intune enforces when the user tries to access or move "corporate" data. It can also define actions that Intune blocks or monitors while the user is in the app.

### What are examples of app protection policies?

For details about each app protection policy setting, see [Android app protection policy settings](ref-settings-android) and [iOS/iPadOS app protection policy settings](ref-settings-ios).

### Is it possible to have both MDM and MAM policies applied to the same user at the same time, for different devices?

If you apply a MAM policy to the user without setting the device management state, the user gets the MAM policy on both the personal device, also known as a bring-your-own-device (BYOD), and the Intune-managed device. You can also apply a MAM policy based on the device management state. So when you create an app protection policy, next to Target to apps on all device types, you'd select No. Then choose one of the following options:

- Apply a less strict MAM policy to Intune managed devices, and apply a more restrictive MAM policy to non MDM-enrolled devices.
- Apply an equally strict MAM policy to Intune-managed devices and to non-Microsoft managed devices.
- Apply a MAM policy to unenrolled devices only.

For more information, see [How to monitor app protection policies](monitor-policies).

## Apps you can manage with app protection policies

### Which apps can be managed by app protection policies?

Any app integrated with the [Intune App SDK](../../developer/app-sdk/) or wrapped by the [Intune App Wrapping Tool](../../developer/app-sdk/integration-methods) can be managed using Intune app protection policies. See the official list of [Intune-managed apps](../ref-protected-apps) available for public use.

### What are the baseline requirements to use app protection policies on an Intune-managed app?

- The end user must have a Microsoft Entra account. For more information on how to create Intune users in Microsoft Entra ID, see [Add users and give administrative permission to Intune](../../fundamentals/tenant-administration/add-users).
- The end user must have a license for Microsoft Intune assigned to their Microsoft Entra account. For more information on how to assign Intune licenses to end users, see [Manage Intune licenses](../../fundamentals/assign-licenses).
- The end user must belong to a security group targeted by an app protection policy. The same app protection policy must target the specific app being used. App protection policies can be created and deployed in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Security groups can currently be created in the [Microsoft 365 admin center](https://admin.microsoft.com).
- The end user must sign into the app using their Microsoft Entra account.

### What if I want to enable an app with Intune App Protection but it isn't using a supported app development platform?

The Intune SDK development team actively tests and maintains support for apps built with the native Android, iOS/iPadOS (Obj-C, Swift), .NET and MAUI platforms. Some customers successfully integrate the Intune SDK with other platforms, such as React Native and NativeScript. However, Microsoft doesn't provide guidance or plugins for platforms other than the supported ones.

### Does the Intune APP SDK support Microsoft Authentication Library (MSAL)?

The Intune App SDK can use the Microsoft Authentication Library for its authentication and conditional launch scenarios. It also relies on MSAL to register the user identity with the MAM service for management without device enrollment scenarios.

### What are the other requirements to use the Outlook mobile app?

- The end user must have the [Outlook mobile app](https://products.office.com/outlook) installed to their device.
- The end user must have a [Microsoft 365 Exchange Online](https://products.office.com/exchange/exchange-online) mailbox and license linked to their Microsoft Entra account.

    Note

    The Outlook mobile app currently only supports Intune App Protection for Microsoft Exchange Online and [Exchange Server with hybrid modern authentication](/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) and doesn't support Exchange in Office 365 Dedicated.

### What are the other requirements to use the Word, Excel, and PowerPoint apps?

- The end user must have a license for [Microsoft 365 Apps for business or enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) linked to their Microsoft Entra account. The subscription must include the Office apps on mobile devices and can include a cloud storage account with [OneDrive cloud storage and file sharing for business](https://onedrive.live.com/about/business/). Microsoft 365 licenses can be assigned in the [Microsoft 365 admin center](https://admin.microsoft.com) following these [instructions](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).
- The end user must have a managed location configured using the granular save as functionality under the "Save copies of org data" application protection policy setting. For example, if the managed location is OneDrive, the [OneDrive](https://onedrive.live.com/about/) app should be configured in the end user's [Word, Excel, or PowerPoint](https://products.office.com/business/office) app.
- If the managed location is OneDrive, the app must be targeted by the app protection policy deployed to the end user.

    Note

    The Office mobile apps currently only support SharePoint Online and not SharePoint on-premises.

### Why is a managed location (that is, OneDrive) needed for Office?

Intune marks all data in the app as either "corporate" or "personal." Data is considered "corporate" when it originates from a business location. For Office apps, Intune treats email (Exchange) and cloud storage (OneDrive) as business locations.

### What are the other requirements to use Skype for Business?

See [Skype for Business](https://products.office.com/skype-for-business/it-pros) license requirements. For Skype for Business (SfB) hybrid and on-premises configurations, see [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) and [Modern Auth for SfB on-premises with Microsoft Entra ID](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910), respectively.

## App protection features

### What is multi-identity support?

Multi-identity support is the ability for the Intune App SDK to only apply app protection policies to the work or school account signed into the app. If a personal account is signed into the app, the data is untouched.

### What is the purpose of multi-identity support?

Multi-identity support allows apps with both "corporate" and consumer audiences (that is, the Office apps) to be released publicly with Intune app protection capabilities for the "corporate" accounts.

### What about Outlook and multi-identity?

Because Outlook has a combined email view of both personal and "corporate" emails, the Outlook app prompts for the Intune PIN on launch.

### What is the Intune app PIN?

The Personal Identification Number (PIN) is a passcode used to verify that the correct user is accessing the organization's data in an application.

### When is the user prompted to enter their PIN?

Intune prompts for the user's app PIN when the user is about to access "corporate" data. In multi-identity apps such as Word/Excel/PowerPoint, the user is prompted for their PIN when they try to open a "corporate" document or file. In single-identity apps, such as line-of-business apps managed using the Intune App Wrapping Tool, the PIN is prompted at launch, because the Intune App SDK knows the user's experience in the app is always "corporate."

### How often are users prompted for the Intune PIN?

The IT admin can define the Intune app protection policy setting 'Recheck the access requirements after (minutes)' in the Microsoft Intune admin center. This setting specifies the amount of time before the access requirements are checked on the device, and the application PIN screen is shown again. However, important details about PIN that affect how often users are prompted are:

- **The PIN is shared among apps of the same publisher to improve usability:** On iOS/iPadOS, one app PIN is shared among all apps **of the same app publisher**. On Android, one app PIN is shared among all apps.
- **The 'Recheck the access requirements after (minutes)' behavior after a device reboot:** A "PIN timer" tracks the number of minutes of inactivity that determine when to show the Intune app PIN next. On iOS/iPadOS, the PIN timer is unaffected by device reboot. Thus, device restart has no effect on the number of minutes the user is inactive from an iOS/iPadOS app with Intune PIN policy. On Android, the PIN timer is reset on device reboot. As such, Android apps with Intune PIN policy will likely prompt for an app PIN regardless of the 'Recheck the access requirements after (minutes)' setting value **after a device reboot**.
- **The rolling nature of the timer associated with the PIN:** Once a PIN is entered to access an app (app A), and the app leaves the foreground (main input focus) on the device, the PIN timer gets reset for that PIN. Any app (app B) that shares this PIN doesn't prompt the user for PIN entry because the timer has reset. The prompt will show up again once the 'Recheck the access requirements after (minutes)' value is met again.

On iOS/iPadOS devices, apps from different publishers can share the same PIN. However, when the **Recheck the access requirements after (minutes)** value is reached, Intune prompts the user for a PIN if the app wasn't the main input focus. So, for example, a user has app *A* from publisher *X* and app *B* from publisher *Y*, and those two apps share the same PIN. The user is focused on app *A* (foreground), and app *B* is minimized. After the **Recheck the access requirements after (minutes)** value is met and the user switches to app *B*, the PIN would be required.

Note

In order to verify the user's access requirements more often (that is, PIN prompt), especially for a frequently used app, reduce the value of the 'Recheck the access requirements after (minutes)' setting.

### How does the Intune PIN work with built-in app PINs for Outlook and OneDrive?

The Intune PIN works based on an inactivity-based timer (the value of 'Recheck the access requirements after (minutes)'). As such, Intune PIN prompts show up independently from the built-in app PIN prompts for Outlook and OneDrive which often are tied to app launch by default. If the user receives both PIN prompts at the same time, the expected behavior should be that the Intune PIN takes precedence.

### Is the PIN secure?

The PIN serves to allow only the correct user to access their organization's data in the app. Therefore, an end user must sign in with their work or school account before they can set or reset their Intune app PIN. Microsoft Entra ID handles this authentication through secure token exchange, and isn't transparent to the Intune App SDK. From a security perspective, the best way to protect work or school data is to encrypt it. Encryption isn't related to the app PIN but is its own app protection policy.

### How does Intune protect the PIN against brute force attacks?

As part of the app PIN policy, the IT administrator can set the maximum number of times a user can try to authenticate their PIN before locking the app. After the number of attempts is met, the Intune App SDK can wipe the "corporate" data in the app.

### Why do I have to set a PIN twice on apps from same publisher?

MAM on iOS/iPadOS supports application-level PINs with alphanumeric and special characters (called a passcode). To enforce passcode settings, apps like Word, Excel, PowerPoint, Outlook, Managed Browser, and Yammer must integrate the Intune App SDK for iOS/iPadOS. Without this integration, Intune can't enforce the passcode settings for those apps. Intune introduced this feature in SDK version 7.1.12 for iOS/iPadOS.  To support this feature and maintain compatibility with earlier versions of the Intune SDK for iOS/iPadOS, version 7.1.12 and later handle all PINs (numeric or passcode) separately from the numeric PIN used in earlier versions. Therefore, if a device has applications with Intune SDK for iOS/iPadOS versions before 7.1.12 AND after 7.1.12 from the same publisher, they'll have to set up two PINs.  That being said, the two PINs (for each app) aren't related in any way. They must adhere to the app protection policy applied to the app. As such, *only* if apps A and B have the same policies applied (with respect to PIN), user could set up the same PIN twice.  This behavior is specific to the PIN on iOS/iPadOS applications that are enabled with Intune Mobile App Management. Over time, as applications adopt later versions of the Intune SDK for iOS/iPadOS, having to set a PIN twice on apps from the same publisher becomes less of an issue.

Note

App versions determine whether a shared PIN is possible. For example, if app A uses an SDK version earlier than 7.1.12 and app B uses version 7.1.12 or later, the user must set up a separate PIN for each app—even if they’re from the same publisher. However, if apps A and C both use pre-7.1.12 versions, they share a PIN. Likewise, apps B and D share a PIN if both use SDK 7.1.12 or later.

### What about encryption?

IT administrators can deploy an app protection policy that requires app data to be encrypted. As part of the policy, the IT administrator can also specify when the content is encrypted.

### How does Intune encrypt data?

Intune encrypts data according to the app protection policy setting for encryption. For details, see [Android app protection policy settings](ref-settings-android) and [iOS/iPadOS app protection policy settings](ref-settings-ios).

### What gets encrypted?

Only data marked as "corporate" is encrypted according to the IT administrator's app protection policy. Data is considered "corporate" when it originates from a business location. For Office apps, Intune treats email (Exchange) and cloud storage (OneDrive) as business locations. For line-of-business apps managed by the Intune App Wrapping Tool, all app data is considered "corporate."

### How does Intune remotely wipe data?

Intune can wipe app data in three different ways: full device wipe, selective wipe for MDM, and MAM selective wipe. For more information about remote wipe for MDM, see [Remove devices by using wipe or retire](../../device-management/actions/wipe). For more information about selective wipe using MAM, see [the Retire action](../../device-management/actions/retire) and [How to wipe only corporate data from apps](wipe-corporate-data).

### What is wipe?

[Wipe](../../device-management/actions/wipe) removes all user data and settings from **the device** by restoring the device to its factory default settings. The device is removed from Intune.

Note

Wipe can only be achieved on devices enrolled with Intune mobile device management (MDM).

### What is selective wipe for MDM?

Selective wipe for MDM removes only company data from the device without affecting personal data. For more information, see [Remove devices - retire](../../device-management/actions/retire).

### What is selective wipe for MAM?

Selective wipe for MAM simply removes company app data from an app. The request is initiated using the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). To learn how to initiate a wipe request, see [How to wipe only corporate data from apps](wipe-corporate-data).

### How quickly does selective wipe for MAM happen?

If the user is using the app when selective wipe is initiated, the Intune App SDK checks every 30 minutes for a selective wipe request from the Intune MAM service. It also checks for selective wipe when the user launches the app for the first time and signs in with their work or school account.

### Why don't on-premises services work with Intune protected apps?

Intune app protection depends on the identity of the user to be consistent between the application and the Intune App SDK. The only way to guarantee that is through modern authentication. There are scenarios in which apps might work with an on-premises configuration, but they're not consistent or guaranteed.

### Is there a secure way to open web links from managed apps?

Yes! The IT administrator can deploy and set app protection policy for the Microsoft Edge app. The IT administrator can require all web links in Intune-managed apps to be opened using the Microsoft Edge app.

## App experience on Android

### Why is the Company Portal app needed for Intune app protection to work on Android devices?

[Company Portal app and Intune app protection](overview#company-portal-app-and-intune-app-protection)

### How do multiple Intune app protection access settings that are configured to the same set of apps and users work on Android?

Intune app protection policies for access are applied in a specific order on end user devices as they try to access a targeted app from their corporate account. In general, a block would take precedence, and then a dismissible warning. For example, if applicable to the specific user/app, a minimum Android patch version setting that warns a user to take a patch upgrade will be applied after the minimum Android patch version setting that blocks the user from access. So, in the scenario where the IT admin configures the min Android patch version to 2018-03-01 and the min Android patch version (Warning only) to 2018-02-01, while the device trying to access the app was on a patch version 2018-01-01, the end user would be blocked based on the more restrictive setting for min Android patch version that results in blocked access.

When dealing with different types of settings, an app version requirement would take precedence, followed by Android operating system version requirement and Android patch version requirement. Then, any warnings for all types of settings in the same order are checked.

### Intune App Protection Policies provide the capability for admins to require end user devices to pass Google Play's device integrity check for Android devices. How often is a new Google Play’s device integrity check result sent to the service?

The Intune service contacts Google Play at a nonconfigurable interval determined by service load. Any IT admin configured action for Google Play’s device integrity check setting will be taken based on the last reported result to the Intune service at the time of conditional launch. If the Google's device integrity result is compliant, no action is taken. If the Google's device integrity result is noncompliant, the IT admin configured action is taken immediately. If the request to Google Play’s device integrity check fails for any reason, the cached result from the previous request will be used for up to 24 hours or the next device restart, which ever comes first. At that time Intune App Protection Policies block access until a current result can be obtained.

### Intune App Protection Policies provide the capability for admins to require end user devices to send signals via Google's Verify Apps API for Android devices. How can an end user turn on the app scan so that they aren't blocked from access due to this?

The instructions on how to do this varies slightly by device. The general process involves going to the Google Play Store, then clicking on **My apps & games**, clicking on the result of the last app scan which will take you into the Play Protect menu. Ensure the toggle for **Scan device for security threats** is switched to on.

### What does Google's Play Integrity API actually check on Android devices? What is the difference between the configurable values of 'Check basic integrity' and 'Check basic integrity & certified devices'?

Intune applies Google Play Integrity APIs to add to our existing root detection checks for unenrolled devices. Google developed and maintained this API set for Android apps to adopt if they don't want their apps to run on rooted devices. The Android Pay app incorporated this, for example. While Google doesn't share publicly the entirety of the root detection checks that occur, we expect these APIs to detect users who have rooted their devices. These users can then be blocked from accessing, or their corporate accounts wiped from their policy enabled apps. 'Check basic integrity' tells you about the general integrity of the device. Rooted devices, emulators, virtual devices, and devices with signs of tampering fail basic integrity. 'Check basic integrity & certified devices' tells you about the compatibility of the device with Google's services. Only unmodified devices that have been certified by Google can pass this check. Devices that fail include:

- Devices that fail basic integrity
- Devices with an unlocked bootloader
- Devices with a custom system image/ROM
- Devices the manufacturer didn't apply for, or pass, Google certification
- Devices with a system image built directly from the Android Open Source Program source files
- Devices with a beta/developer preview system image

See [Google's documentation on Play Integrity API](https://developer.android.com/google/play/integrity) for technical details.

### There are two similar checks in the Conditional Launch section when creating an Intune App Protection Policy for Android devices. Should I be requiring the 'Play integrity verdict' setting or the 'jailbroken/rooted devices' setting?

Google Play Integrity API checks require the end user being online, atleast during the time when the "roundtrip" for determining attestation results executes. If end user is offline, IT admin can still expect a result to be enforced from the 'jailbroken/rooted devices' setting. That being said, if the end user has been offline too long, the 'Offline grace period' value comes into play, and all access to work or school data is blocked once that timer value is reached, until network access is available. Turning on both settings allows for a layered approach to keeping end user devices healthy which is important when end users access work or school data on mobile.

### The app protection policy settings that apply Google Play Protect APIs require Google Play Services to function. What if Google Play Services aren't allowed in the location where the end user might be?

Both the 'Play integrity verdict,' and 'Threat scan on apps' settings require Google determined version of Google Play Services to function correctly. Since these are settings that fall in the area of security, the end user is blocked if they're targeted with these settings and aren't meeting the appropriate version of Google Play Services or have no access to Google Play Services.

## App experience on iOS

### What happens if I add or remove a fingerprint or face to my device?

Intune app protection policies allow control over app access to only the Intune licensed user. One of the ways to control access to the app is to require either Apple's Touch ID or Face ID on supported devices. Intune implements a behavior where if there's any change to the device's biometric database, Intune prompts the user for a PIN when the next inactivity timeout value is met. Changes to biometric data include the addition or removal of a fingerprint, or face. If the Intune user doesn't have a PIN set, they're led to set up an Intune PIN.

The intent of this is to continue keeping your organization's data within the app secure and protected at the app level. This feature is only available for iOS/iPadOS, and requires the participation of applications that integrate the Intune APP SDK for iOS/iPadOS, version 9.0.1 or later. Integration of the SDK is necessary so that the behavior can be enforced on the targeted applications. This integration happens on a rolling basis and is dependent on the specific application teams. Some apps that participate include WXP, Outlook, Managed Browser, and Yammer.

### I'm able to use the iOS share extension to open work or school data in unmanaged apps, even with the data transfer policy set to "managed apps only" or "no apps." Doesn't this leak data?

Intune app protection policy can't control the iOS share extension without managing the device. Therefore, Intune ***encrypts "corporate" data before it's shared outside the app***. You can validate this by attempting to open the "corporate" file outside of the managed app. The file should be encrypted and unable to be opened outside the managed app.

### How do multiple Intune app protection access settings that are configured to the same set of apps and users work on iOS?

Intune app protection policies for access will be applied in a specific order on end user devices as they try to access a targeted app from their corporate account. In general, a wipe would take precedence, followed by a block, and then a dismissible warning. For example, if applicable to the specific user/app, a minimum iOS/iPadOS operating system setting that warns a user to update their iOS/iPadOS version will be applied after the minimum iOS/iPadOS operating system setting that blocks the user from access. So, in the scenario where the IT admin configures the min iOS/iPadOS operating system to 11.0.0.0 and the min iOS/iPadOS operating system (Warning only) to 11.1.0.0, while the device trying to access the app was on iOS/iPadOS 10, the end user would be blocked based on the more restrictive setting for min iOS/iPadOS operating system version that results in blocked access.

When dealing with different types of settings, an Intune App SDK version requirement would take precedence, and then an app version requirement, followed by the iOS/iPadOS operating system version requirement. Then, any warnings for all types of settings in the same order are checked. We recommend the Intune App SDK version requirement be configured only upon guidance from the Intune product team for essential blocking scenarios.