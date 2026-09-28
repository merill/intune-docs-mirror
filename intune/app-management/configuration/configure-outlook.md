---
layout: Conceptual
title: Manage Outlook for iOS and Android With Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-outlook
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Android
ms.subservice: apps
description: Use Intune app protection and configuration policies with Outlook for iOS and Android to ensure team collaboration experiences are always accessed with safeguards in place.
ms.date: 2025-06-12T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: 95a77a7c-d56e-89d3-1df9-c1e8ddb16844
document_version_independent_id: 95a77a7c-d56e-89d3-1df9-c1e8ddb16844
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/configure-outlook.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/configure-outlook
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/configure-outlook.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
- https://authoring-docs-microsoft.poolparty.biz/devrel/cf9b82c5-b6dc-45f3-b005-b1bc5fc03bea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
- https://authoring-docs-microsoft.poolparty.biz/devrel/0c85d34e-bfd2-4466-957c-f0b61e9692df
platformId: ca326dcb-0726-da6d-b8c1-f072611d3086
---

# Manage Outlook for iOS and Android With Intune - Microsoft Intune | Microsoft Learn

The Outlook for iOS and Android app is designed to enable users in your organization to do more from their mobile devices, by bringing together email, calendar, contacts, and other files.

The richest and broadest protection capabilities for Microsoft 365 data are available when you subscribe to the Enterprise Mobility + Security suite, which includes Microsoft Intune and Microsoft Entra ID P1 or P2 features, such as Conditional Access. At a minimum, you will want to deploy a Conditional Access policy that allows connectivity to Outlook for iOS and Android from mobile devices and an Intune app protection policy that ensures the collaboration experience is protected.

## Apply Conditional Access

Organizations can use Microsoft Entra Conditional Access policies to ensure that users can only access work or school content using Outlook for iOS and Android. To do this, you will need a Conditional Access policy that targets all potential users. These policies are described in [Conditional Access: Require approved client apps or app protection policy](/en-us/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection).

1. Follow the steps in [Require approved client apps or app protection policy with mobile devices](/en-us/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices). This policy allows Outlook for iOS and Android, but blocks OAuth and basic authentication capable Exchange ActiveSync mobile clients from connecting to Exchange Online.

    Note

    This policy ensures mobile users can access all Microsoft 365 endpoints using the applicable apps.
2. Follow the steps in [Block Exchange ActiveSync on all devices](/en-us/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices), which prevents Exchange ActiveSync clients using basic authentication on non-mobile devices from connecting to Exchange Online.

    The above policies leverage the grant access control [Require app protection policy](/en-us/azure/active-directory/active-directory-conditional-access-technical-reference), which ensures that an Intune App Protection Policy is applied to the associated account within Outlook for iOS and Android prior to granting access. If the user isn't assigned to an Intune App Protection Policy, isn't licensed for Intune, or the app isn't included in the Intune App Protection Policy, then the policy prevents the user from obtaining an access token and gaining access to messaging data.
3. Follow the steps in [How to: Block legacy authentication to Microsoft Entra ID with Conditional Access](/en-us/azure/active-directory/conditional-access/block-legacy-authentication) to block legacy authentication for other Exchange protocols on iOS and Android devices; this policy should target only Microsoft Exchange Online cloud app and iOS and Android device platforms. This ensures mobile apps using Exchange Web Services, IMAP4, or POP3 protocols with basic authentication cannot connect to Exchange Online.

Note

To leverage app-based Conditional Access policies, the Microsoft Authenticator app must be installed on iOS devices. For Android devices, the Intune Company Portal app is required. For more information, see [App-based Conditional Access with Intune](../../device-security/conditional-access-integration/app-based-policies).

## Create Intune app protection policies

App protection policies define which apps are allowed and the actions they can take with your organization's data. The choices available in app protection policies enable organizations to tailor the protection to their specific needs. For some, it may not be obvious which policy settings are required to implement a complete scenario. To help organizations prioritize mobile client endpoint hardening, Microsoft has introduced taxonomy for its app protection policies data protection framework for iOS and Android mobile app management.

The app protection policies data protection framework is organized into three distinct configuration levels, with each level building off the previous level:

- **Enterprise basic data protection** (Level 1) ensures that apps are protected with a PIN and encrypted and performs selective wipe operations. For Android devices, this level validates Android device attestation. This is an entry level configuration that provides similar data protection control in Exchange Online mailbox policies and introduces IT and the user population to APP.
- **Enterprise enhanced data protection** (Level 2) introduces app protection policies data leakage prevention mechanisms and minimum OS requirements. This is the configuration that is applicable to most mobile users accessing work or school data.
- **Enterprise high data protection** (Level 3) introduces advanced data protection mechanisms, enhanced PIN configuration, and app protection policies Mobile Threat Defense. This configuration is desirable for users that are accessing high risk data.

To see the specific recommendations for each configuration level and the minimum apps that must be protected, review [Data protection framework using app protection policies](../protection/data-protection-framework).

Regardless of whether the device is enrolled in a unified endpoint management (UEM) solution, an Intune app protection policy needs to be created for both iOS and Android apps, using the steps in [How to create and assign app protection policies](../protection/create-policy). These policies, at a minimum, must meet the following conditions:

- They include all Microsoft 365 mobile applications, such as Edge, Outlook, OneDrive, Office, or Teams, as this ensures that users can access and manipulate work or school data within any Microsoft app in a secure fashion.
- They are assigned to all users. This ensures that all users are protected, regardless of whether they use Outlook for iOS or Android.
- Determine which framework level meets your requirements. Most organizations should implement the settings defined in **Enterprise enhanced data protection** (Level 2) as that enables data protection and access requirements controls.

For more information on the available settings, see [Android app protection policy settings](../protection/ref-settings-android) and [iOS app protection policy settings](../protection/ref-settings-ios).

Important

To apply Intune app protection policies against apps on Android devices that are not enrolled in Intune, the user must also install the Intune Company Portal.

## Use app configuration

Outlook for iOS and Android supports app settings that allow unified endpoint management administrators to customize the behavior of the app. Microsoft Intune, which is a unified endpoint management solution, is commonly used to configure and assign apps to organizational end users.

App configuration can be delivered either through the mobile device management (MDM) OS channel on enrolled devices ([Managed App Configuration](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html) channel for iOS or the [Android in the Enterprise](https://developer.android.com/work/managed-configurations) channel for Android) or through the Intune App Protection Policy (APP) channel. Outlook for iOS and Android supports the following configuration scenarios:

- Only allow work or school accounts
- General app configuration settings
- S/MIME settings
- Data protection settings

For specific procedural steps and detailed documentation on the app configuration settings Outlook for iOS and Android supports, see [Deploying Outlook for iOS and Android app configuration settings](/en-us/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).