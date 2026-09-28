---
layout: Conceptual
title: Set up just-in-time registration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-just-in-time-registration
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: rishitasarin
ms.subservice: enrollment
description: Set up JIT registration in Intune for devices enrolling via a supported Apple device enrollment or user enrollment method.
ms.date: 2024-07-22T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: c1441a80-486e-b886-0201-af24bb7203c6
document_version_independent_id: c1441a80-486e-b886-0201-af24bb7203c6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-just-in-time-registration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-just-in-time-registration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-just-in-time-registration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
platformId: b6ba4918-1fa2-e1ad-9514-5e7f60d8901b
---

# Set up just-in-time registration - Microsoft Intune | Microsoft Learn

**Applies to iOS/iPadOS**

Set up *just-in-time (JIT) registration* in Microsoft Intune to enable device users to initiate and complete device enrollment from a work or school app. The Intune Company Portal isn't required when using JIT registration. Instead, JIT registration utilizes the Apple single sign-on (SSO) extension to complete Microsoft Entra registration and compliance checks. Registration and compliance checks can be fully integrated in a designated Microsoft or non-Microsoft app that's configured with the Apple single sign-on (SSO) app extension. The extension reduces authentication prompts during the device user's session and establishes SSO across the whole device.

JIT compliance remediation, the feature that initiates compliance checks, is enabled automatically on devices utilizing JIT registration and targeted with compliance policies. Compliance remediation happens in an embedded flow within the app users are registering. They can see their compliance status and take actionable steps to remediate the issues as they complete JIT registration. If their device is noncompliant, for example, the Company Portal website opens in the app and shows them the reason for noncompliance.

This article describes how to enable JIT registration by creating an SSO app extension policy in the Microsoft Intune admin center.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - iOS/iPadOS
> 

![](../../media/icons/16/enrollment.svg)**Enrollment methods**

> 
> Microsoft Intune supports JIT registration and compliance remediation for all iOS and iPadOS enrollments, including:
> 
> - Apple User Enrollment: Account-driven user enrollment and user enrollment with Company Portal
> - Apple Device Enrollment: Web-based device enrollment and device enrollment with Company Portal
> - Apple automated device enrollment: For enrollments that use Setup Assistant with modern authentication as the [authentication method](ref-automated-authentication-methods)
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To take advantage of JIT compliance remediation, you must assign compliance policies to devices.

## Best practices for SSO configuration

- The user's first sign-in after they reach the home screen has to happen in a work or school app that's configured with the SSO extension. Otherwise, Microsoft Entra registration and compliance checks can't be completed. We recommend that you point employees to the Microsoft Teams app. The app is integrated with the latest identity libraries and provides the most streamlined experience from the user's home screen.
- The SSO extension automatically applies to all Microsoft apps, so to avoid authentication problems, don't add the bundle IDs for your Microsoft apps to your policy. You only need to add non-Microsoft apps.
- Don't add the bundle ID for the Microsoft Authenticator app to your SSO extension policy. Since it's a Microsoft app, the SSO extension will automatically work with it.

## Set up JIT registration

Create a single sign-on app extension policy that uses the Apple SSO extension to enable just-in-time (JIT) registration.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. [Create an iOS/iPadOS device configuration policy](../../device-configuration/templates/configure-device-features-apple) under **Device features** &gt; **Category** &gt; [**Single sign-on app extension**](../../device-configuration/templates/configure-device-features-apple#single-sign-on-sso).
3. For **SSO app extension type**, select **Microsoft Entra ID**.
4. Add the [app bundle IDs](../../device-configuration/templates/ref-bundle-ids-ios) for any non-Microsoft apps using single sign-on (SSO). The SSO extension automatically applies to all Microsoft apps, so to avoid authentication problems, don't add Microsoft apps to your policy.

    Don't add the Microsoft Authenticator app to the SSO extension either. That app is added later in an app policy.

    To get the bundle ID of an app added to Intune, [you can use the Intune admin center](../../app-management/collect-bundle-ids).
5. Under **Additional configuration**, add the required key-value pair. Remove trailing spaces before and after the value and key. Otherwise just-in-time registration won't work.

    - **Key**: device\_registration
    - **Type**: String
    - **Value**: {{DEVICEREGISTRATION}}
6. (Recommended) Add the key-value pair that enables SSO in the Safari browser for all apps in the policy. Remove trailing spaces before and after the value and key. Otherwise just-in-time registration won't work.

    - **Key**: browser\_sso\_interaction\_enabled
    - **Type**: Integer
    - **Value**: 1
7. Select **Next**.
8. For **Assignments**, assign the profile to all users, or select specific groups.
9. Select **Next**.
10. On the **Review + create** page, review your choices, and then select **Create** to finish creating the profile.
11. Go to **Apps** &gt; **All Apps** and assign Microsoft Authenticator to groups as a required app. For more information, see [Add apps to Microsoft Intune](../../app-management/deployment/) and [Assign apps to groups](../../app-management/deployment/assign-groups).