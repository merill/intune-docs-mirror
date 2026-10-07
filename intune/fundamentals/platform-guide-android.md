---
layout: Conceptual
title: Deployment guide to manage Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn the recommended processes to manage Android devices in Microsoft Intune.
ms.date: 2025-04-15T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.reviewer: cchristenson
locale: en-us
document_id: 97f03449-3c57-7fdb-6d07-60d7a86ed3cb
document_version_independent_id: 97f03449-3c57-7fdb-6d07-60d7a86ed3cb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/platform-guide-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/platform-guide-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/platform-guide-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 7dbc2636-29bf-6ea6-14b4-d529eb9ce3d8
---

# Deployment guide to manage Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Intune supports the mobile device management (MDM) of Android devices to give people secure access to work email, data, and apps. This guide provides Android-specific resources to help you set up enrollment in Intune and deploy apps and policies to users and devices.

## Prerequisites

Before you begin, complete these prerequisites to enable Android device management in Intune. For more detailed information about how to set up, onboard, or move to Intune, see the [Intune setup deployment guide](setup-migration).

- [Add users](tenant-administration/add-users) and [groups](tenant-administration/add-groups)
- [Assign licenses to users](assign-licenses)
- [Set mobile device management authority](setup-mdm-authority)

We recommend you use the least privileged role that's needed to complete tasks. For example, the least privileged role that can complete device enrollment tasks is the built-in **Policy and Profile Manager** Intune role.

For more information on the built-in roles and what they can do, see [Role-based access control (RBAC) with Intune](role-based-access-control/overview) and [Built-in role permissions for Intune](role-based-access-control/ref-built-in-roles).

## Plan for your deployment

Use the [Microsoft Intune planning guide](planning-guide) for help with planning, designing, and implementing Microsoft Intune in your organization. The guide provides information to help you:

- Determine goals, use-case scenarios, and requirements.
- Create rollout and communication plans.
- Create support, testing, and validation plans.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Create compliance rules

Use compliance policies to define the rules and conditions that users and devices should meet to access your organization's protected resources. You can also create Conditional Access policies, which work alongside your device compliance results to block access to resources from noncompliant devices. For a detailed explanation about compliance policies and how to get started, see [Use compliance policies to set rules for devices you manage with Intune](../device-security/compliance/overview).

The following tasks apply to both Android Enterprise and Android device administrator platforms.

| Task | Detail |
| --- | --- |
| [Create a compliance policy](../device-security/compliance/create-policy) | Get step-by-step guidance on how to create and assign a compliance policy to user and device groups. |
| [Add actions for noncompliance](../device-security/compliance/configure-noncompliance-actions) | Choose what happens when devices no longer meet the conditions of your compliance policy. You can add actions for noncompliance when you configure a device compliance policy, or later by editing the policy. |
| Create [a device-based](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) or [app-based](../device-security/conditional-access-integration/create-app-based-policy) Conditional Access policy. | Specify the app or services you want to protect and define the conditions for access. |
| [Block access to apps that don't use modern authentication](../device-security/conditional-access-integration/block-no-modern-auth) | Create an app-based Conditional Access policy to block apps that use authentication methods other than OAuth2. For example, you can block apps that use basic and form-based authentication. Before you block any access, sign in to Microsoft Entra ID and review the [authentication methods activity report](/en-us/azure/active-directory/authentication/howto-authentication-methods-activity) to see if users are using basic authentication to access essential things (like meeting room calendar kiosks) you forgot about or are unaware of. |

## Configure endpoint security

Use the Intune endpoint security features to configure device security and to manage security tasks for devices at risk.

The following tasks apply to both Android Enterprise and Android device administrator platforms.

| Task | Detail |
| --- | --- |
| [Manage devices with endpoint security features](../device-security/endpoint-security-devices) | Use the **Endpoint security** settings in Intune to effectively manage device security and remediate issues for devices. |
| [Enable the mobile threat defense (MTD) connector for enrolled devices](../device-security/mobile-threat-defense/enable-connector) | Enable the MTD connection in Intune so that MTD partner apps can work with Intune and your MTD device compliance policies. If you're not using Microsoft Defender for Endpoint, consider enabling the connector so that you can use another mobile threat defense solution. You can also [enable the MTD connector for devices not enrolled in Intune](../device-security/mobile-threat-defense/enable-unenrolled-devices). |
| [Create MTD app protection policy](../device-security/mobile-threat-defense/create-app-protection-policy) | Create an Intune app protection policy that assesses risks and limits a device's access to work or school apps. |
| [Create MTD device compliance policy](../device-security/mobile-threat-defense/create-compliance-policy) | Create an Intune app protection policy that assesses risk and limits a device's corporate access based on the threat level. |
| [Add and assign MTD apps](../device-security/mobile-threat-defense/assign-apps) | Add and deploy MTD apps in Intune. These apps work with your device compliance and app protection policies to identify and help remediate device threats. You can also [assign MTD apps to devices not enrolled in Intune](../device-security/mobile-threat-defense/add-apps-unenrolled-devices). |

## Configure device settings

Use Microsoft Intune to enable or disable settings and features on devices. To configure and enforce these settings, create a device profile and then assign the profile to groups in your organization. Devices receive the profile once they enroll.

| Task | Detail | Platform |
| --- | --- | --- |
| [Create a device profile in Microsoft Intune](../device-configuration/create-device-profile) | Learn about the different types of device profiles you can create for your organization. | Android Enterprise, Android device administrator |
| [Configure Wi-Fi profile](../device-configuration/templates/configure-wifi) | This profile enables people to find and connect to your organization's Wi-Fi network. For a description of the settings in this area, see the Wi-Fi settings reference for [Android Enterprise Wi-Fi settings](../device-configuration/templates/ref-wifi-settings-android-enterprise) or [Android device administrator Wi-Fi settings](../device-configuration/templates/ref-wifi-settings-android). | Android Enterprise, Android device administrator |
| [Configure VPN profile](../device-configuration/templates/configure-vpn) | Set up a secure VPN option, such as Microsoft Tunnel, for people connecting to your organization's network. For a description of the settings in this area, see the VPN settings reference for [Android Enterprise VPN settings](../device-configuration/templates/ref-vpn-settings-android-enterprise) or [Android device administrator VPN settings](../device-configuration/templates/ref-vpn-settings-android). | Android Enterprise, Android device administrator |
| [Configure email profile](../device-configuration/templates/configure-email) | Configure email settings so that people can connect to a mail server and access their work or school email. For a description of the settings in this area, see [Android Enterprise email settings](../device-configuration/templates/ref-email-settings-android-enterprise) or [Android device administrator email settings](../device-configuration/templates/ref-email-settings-android). | Android Enterprise, Android device administrator |
| [Restrict device features](../device-configuration/templates/configure-device-restrictions) | Protect users from unauthorized access and distractions by limiting the device features they can use at work or school. For a description of the settings in this area, see [Android Enterprise device settings](../device-configuration/templates/ref-device-restrictions-android-enterprise) or [Android device administrator device settings](../device-configuration/templates/ref-device-restrictions-android). | Android Enterprise, Android device administrator |
| [Configure custom settings for Android device administrator](../device-configuration/templates/configure-custom-settings-android) | Add or create custom settings that aren't built in to Intune, such as a per-app VPN profile and web protection with Microsoft Defender for Endpoint. | Android device administrator |
| [Configure Samsung Knox apps](../device-configuration/templates/manage-apps-samsung-knox) | Create a custom profile to allow and block apps for Samsung Knox Standard devices. | Android device administrator |
| [Configure Zebra Mobility Extensions (MX) profile](../device-configuration/templates/configure-zebra-mx-android) | Use Zebra's Mobility Extensions (MX) profiles to customize or add more Zebra-specific settings in Intune. | Android device administrator |
| [Create OEMConfig configuration profile](../device-configuration/templates/configure-oemconfig-android) | Use OEMConfig to add, create, and customize OEM-specific settings for Android Enterprise devices. | Android Enterprise |
| [Customize branding and enrollment experience](../app-management/configuration/configure-company-portal) | Customize the Intune Company Portal and Microsoft Intune apps with your organization's branding to create a familiar experience for people enrolling their devices. | Android Enterprise, Android device administrator |

## Set up secure authentication methods

Set up authentication methods in Intune to ensure that only authorized people access your internal resources. Intune supports multi-factor authentication, SCEP and PKCS certificates, and derived credentials. Certificates can also be used for signing and encryption of email using S/MIME.

| Task | Detail | Platform |
| --- | --- | --- |
| [Require multi-factor authentication (MFA)](../device-enrollment/configure-multifactor-authentication) | Require people to supply two forms of credentials at time of enrollment. | Android Enterprise |
| [Create a trusted certificate profile](../device-configuration/certificates/trusted-root-profiles) | Create and deploy a trusted certificate profile before you create a SCEP, PKCS, or PKCS imported certificate profile. The trusted certificate profile deploys the trusted root certificate to devices using SCEP, PKCS, and PKCS imported certificates. | Android Enterprise, Android device administrator |
| [Use SCEP certificates with Intune](certificates/scep-infrastructure) | Learn what's needed to use SCEP certificates with Intune, and configure the required infrastructure. After you do that, you can [create a SCEP certificate profile](../device-configuration/certificates/scep-profiles) or [set up a third-party certification authority with SCEP](certificates/third-party-ca-scep). | Android Enterprise |
| [Use PKCS certificates with Intune](../device-configuration/certificates/pkcs-profiles) | Configure required infrastructure (such as on-premises certificate connectors), export a PKCS certificate, and add the certificate to an Intune device configuration profile. | Android Enterprise, Android device administrator |
| [Use imported PKCS certificates with Intune](../device-configuration/certificates/imported-pfx-profiles) | Set up imported PKCS certificates, which enable you to [set up and use S/MIME to encrypt email](../device-security/certificates/s-mime). | Android Enterprise, Android device administrator |
| [Set up a derived credentials issuer](../device-security/certificates/derived-credentials) | Provision Android devices with certificates that are derived from user smart cards. | Android Enterprise |

## Deploy apps

As you set up apps and app policies, think about your organization's requirements, such as the platforms you'll support, the tasks people need to do, the type of apps they need to complete those tasks, and the groups who need those apps. You can use Intune to manage the whole device (including apps) or use Intune to manage apps only.

| Task | Detail | Platform |
| --- | --- | --- |
| [Add Google Play Store apps](../app-management/deployment/add-store-android) | Add Android apps from the Google Play Store. | Android device administrator |
| [Add managed Google Play apps](../app-management/deployment/add-managed-google-play) | Add store apps, line-of-business (LOB) apps, and web apps through the managed Google Play Store. | Android Enterprise |
| [Add Android Enterprise system apps](../app-management/configuration/manage-system-apps-android) | Use Intune to enable and disable Android Enterprise system apps. | Android Enterprise |
| [Add web apps](../app-management/deployment/add-web) | Add web apps to Intune and assign to groups. | Android device administrator |
| [Add built-in apps](../app-management/deployment/add-built-in) | Add built-in apps to Intune and assign to groups. | Android device administrator |
| [Add line-of-business apps](../app-management/deployment/add-lob-android) | Add Android line-of-business (LOB) apps to Intune and assign to groups. | Android device administrator |
| [Assign apps to groups](../app-management/deployment/assign-groups) | Assign apps to users and devices. | Android Enterprise, Android device administrator |
| [Include and exclude app assignments](../app-management/deployment/configure-assignment-scope) | Control access and availability to an app by including and excluding selected groups from assignment. | Android Enterprise, Android device administrator |
| [Create an Android app protection policy](../app-management/protection/create-policy) | Keep your organization's data contained within managed apps like Outlook and Word. For details about each setting, see [Android app protection policy settings](../app-management/protection/ref-settings-android). | Android Enterprise, Android device administrator |
| [Validate your app protection policy](../app-management/protection/validate-policy-setup) | Validate that your app protection policy is correctly set up and working before deploying it org-wide. | Android Enterprise, Android device administrator |
| [Create an app configuration policy](../app-management/configuration/configure-managed-android) | Apply custom configuration settings to Android apps on enrolled devices. You can also apply these types of policies [to managed apps, without device enrollment](../app-management/configuration/configure-managed-apps). | Android Enterprise, Android device administrator |
| [Configure Microsoft Edge](../app-management/configuration/configure-edge-ios-android) | Use Intune app protection and configuration policies with Microsoft Edge for Android to ensure that corporate websites are accessed with safeguards in place. | Android Enterprise, Android device administrator |
| [Configure Google Chrome](../app-management/configuration/configure-chrome-android) | Use an Intune app configuration policy to configure Google Chrome on Android devices enrolled in Intune. | Android Enterprise |
| [Configure Microsoft Managed Home Screen app](../app-management/configuration/configure-managed-home-screen) | Set up Managed Home Screen on corporate-owned Android Enterprise dedicated devices enrolled via Intune and running in multi-app kiosk mode. | Android Enterprise |
| [Configure Microsoft Launcher app](../app-management/configuration/configure-launcher-android) | Configure Microsoft Launcher to customize the home screen experience on your organization's fully managed devices. | Android Enterprise |
| [Configure Microsoft Office apps](../app-management/configuration/configure-microsoft-365-mobile) | Use Intune app protection and configuration policies with Office apps to ensure that corporate files are accessed with safeguards in place. | Android Enterprise |
| [Configure Microsoft Teams](../app-management/configuration/configure-teams-mobile) | Use Intune app protection and configuration policies with Teams to ensure that collaborative team experiences are accessed with safeguards in place. | Android Enterprise |
| [Configure Microsoft Outlook](../app-management/configuration/configure-outlook) | Use Intune app protection and configuration policies with Outlook to ensure corporate email and calendars are accessed with safeguards in place. | Android Enterprise |

## Enroll devices

Enrolling devices allows them to receive the policies you create, so have your Microsoft Entra user groups and device groups ready.

Intune supports the following enrollment methods for Android devices:

- Bring-your-own-device (BYOD): Android Enterprise personally owned devices with a work profile
- Android Enterprise corporate owned dedicated devices
- Android Enterprise corporate owned fully managed
- Android Enterprise corporate owned work profile
- Android device administrator

For information about each enrollment method and how to choose one that's right for your organization, see the [Android device enrollment guide for Microsoft Intune](../device-enrollment/android/guide).

| Task | Detail | Platform |
| --- | --- | --- |
| [Connect Intune account to managed Google Play account](../device-enrollment/android/connect-managed-google-play) | To enable Android Enterprise management in Intune, connect your Intune tenant account to your managed Google Play account. | Android Enterprise |
| [Set up work profile enrollment for personally owned devices](../device-enrollment/android/setup-personal-work-profile) | Set up work profile management for personally owned devices. This enrollment method creates a separate area on the device for work-related data so that personal things remain unaffected. | Android Enterprise |
| [Set up work profile enrollment for corporate-owned devices](../device-enrollment/android/setup-corporate-work-profile) | Set up work profile management for corporate-owned devices intended for work and personal use. This enrollment method creates a separate area on the device for work-related data so that personal things remain unaffected. | Android Enterprise |
| [Set up enrollment for dedicated devices](../device-enrollment/android/setup-dedicated) | Set up enrollment for corporate-owned, single-use, kiosk-style devices. | Android Enterprise |
| [Set up enrollment for fully managed devices](../device-enrollment/android/setup-fully-managed) | Set up enrollment for corporate-owned devices that are associated with a single user and used exclusively for work. | Android Enterprise |
| [Enroll dedicated, fully managed, or corporate-owned work-profile devices](../device-enrollment/android/ref-corporate-methods) | After you've set up Intune for Android Enterprise enrollment, enroll devices using one of the five supported enrollment methods. | Android Enterprise |
| [Set up device administrator enrollment](../device-enrollment/android/manage-device-administrator) | Set up Android device administrator enrollment. This method of managing devices has been superseded by Android Enterprise, so we don't recommend enrolling new devices this way. | Android device administrator |
| [Use Samsung Knox Mobile Enrollment to automatically enroll Android devices](../device-enrollment/android/setup-samsung-knox-mobile) | Set up Intune for Samsung Knox Mobile Enrollment (KME), which enables you to automatically enroll large numbers of corporate-owned Android devices. | Android Enterprise, Android device administrator |
| [Identify devices as corporate-owned](../device-enrollment/add-corporate-identifiers) | Assign corporate-owned status to devices to enable more management and identification capabilities in Intune. | Android Enterprise, Android device administrator |
| [Change device ownership](../device-enrollment/add-corporate-identifiers#change-device-ownership) | After a device has been enrolled, you can change its ownership label in Intune to corporate-owned or personal-owned. This adjustment changes the way you can manage the device. | Android Enterprise, Android device administrator |
| [Troubleshoot enrollment problems](/en-us/troubleshoot/mem/intune/troubleshoot-android-enrollment) | Troubleshoot and find resolutions to problems that occur during enrollment. | Android Enterprise, Android device administrator |

## Run remote actions

After devices are set up, you can use remote actions in Intune to manage and troubleshoot devices from a distance. Availability varies by device platform. If an action is absent or disabled in the portal, then it isn't supported on the device.

| Task | Detail |
| --- | --- |
| [Run remote actions in Intune](../device-management/actions/) | Learn how to drill down and remotely manage and troubleshoot individual devices in Intune. This article lists all remote actions available in Intune and links to those procedures. |
| [Remediate vulnerabilities identified by Microsoft Defender for Endpoint](../device-security/microsoft-defender/remediate-vulnerabilities) | Integrate Intune with Microsoft Defender for Endpoint to take advantage of Defender's threat and vulnerability management, and use Intune to remediate endpoint weakness identified by Defender's vulnerability management capability. |
| [Wipe corporate data from Intune-managed apps](../app-management/protection/wipe-corporate-data) | Selectively remove work-related data from a device. |