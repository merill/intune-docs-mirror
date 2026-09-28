---
layout: Conceptual
title: Device staging overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/device-staging
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
description: An overview of device staging, Android Enterprise token types, and token management in Microsoft Intune.
ms.date: 2025-06-04T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilson
locale: en-us
document_id: 542a69b9-d79b-973f-1ef9-4d71a9a858a5
document_version_independent_id: 542a69b9-d79b-973f-1ef9-4d71a9a858a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/device-staging.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/device-staging
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/device-staging.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 7290e360-03c4-efee-ff50-e017a1e740f3
---

# Device staging overview - Microsoft Intune | Microsoft Learn

**Applies to Android**

Enable device staging during enrollment to reduce end user steps for frontline workers and optimize productivity. During device staging, you or a third-party vendor can complete both the admin and end user stages of pre-provisioning. Minimal interaction is required of the user when they receive their device.

Device staging uses a *staging* token during the enrollment process rather than the *default* token type.

This article provides an overview of device staging, token types, and token management in the Microsoft Intune admin center.

## Requirements

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Android Enterprise devices running Android 8 or later.

![](../../media/icons/16/enrollment.svg)**Enrollment methods**

> 
> Device staging is supported for the following enrollment profiles:
> 
> - Android Enterprise corporate-owned fully managed
> - Android Enterprise corporate-owned work profile
> 

## Token types

When you create an enrollment profile in the admin center for one of the supported management types, you have to select the token type. Your options include the default token and the staging token. Each type enables a different enrollment experience.

### Staging token

The *staging* token enables a staged version of the enrollment flow so that you or a third-party vendor can complete the admin *and* end user steps. This process requires more work from the admin or third party vendor than the end user.

There are three stages during this process:

- Stage 1 - Completed by admin
- Stage 2 - Completed by admin or third-party vendor
- Stage 3 - Completed by end users

The device is userless in stage 1 and stage 2. It becomes user affiliated during the last stage. End users complete the last stage when they get the device and sign in to the Microsoft Intune app with their work or school account. Devices are ready to use after sign-in.

In the first stage, an Intune admin completes the following steps:

1. Create the enrollment profile and staging enrollment token in the admin center.
2. Set the token's expiration date.
3. Optionally, in the admin center, create a dynamic device group or an assignment filter. Then assign policies and apps, which reach the device after stage 3.

In the second stage, an Intune admin or third-party vendor completes the following steps:

1. Unbox, assemble, and power on the new device you're enrolling.
2. With the device, scan the staging token's QR code or enter the token string.

Note

Manual token entry isn't supported on Android Enterprise corporate-owned work profile (also known as COPE) devices running Android 11 and later.

1. Complete the enrollment steps and setup wizard. At the end of setup, you are on the device's home screen.
2. Turn off the device and distribute it to the end user.

During stage 2, the Intune assignment filter on the all devices group is the only available option for targeting policies and apps. After the final stage ends, you can use other supported targeting options. Example: User security groups and dynamic groups

In the third, and final stage, an end user completes the following steps:

1. Power on the device.
2. Open the Microsoft Intune app, and then sign in with your work or school account.
3. Complete the remaining enrollment steps. When enrollment is done, the device is ready for use at work or school.

Note

Screens that don’t require end user input can be skipped, depending on technical feasibility. An *enrollment in progress* screen takes their place.

### Default token

The *default* token enables the standard enrollment flow, with two stages of pre-provisioning:

- Stage 1 - Completed by admin
- Stage 2 - Completed by end users

With this token, end users complete most of the pre-provisioning steps. As the admin, you complete a portion of the pre-provisioning steps before you distribute the devices to your workforce. Device users complete the remaining steps when they sign in with their work or school account.

In the first stage, an Intune admin completes the following steps:

1. Create an enrollment profile with the default enrollment token.
2. With the new device, scan the QR code, and then follow the on-screen prompts to configure the device.
3. For a device enrolling with a newly created enrollment token, create a dynamic device group or an assignment filter to assign policies and apps in the user stage.
4. Distribute the device to the end user.

In the second, and final stage, an end user completes the following steps:

1. Unbox the device and connect to Wi-Fi.
2. Sign in to work or school account, and then follow the on-screen prompts.
3. Complete the pre-provisioning steps. If they're going through work profile enrollment, for example, they create and install the work profile.
4. Grant app permissions or accept terms wherever required.

For detailed steps, see:

- [Set up enrollment for Android Enterprise fully managed devices](setup-fully-managed)
- [Set up enrollment for corporate-owned work profile devices](setup-corporate-work-profile)

## Replace, remove, or export token

Select your token in the admin center to access token management options:

- **Replace token**: Generate a new token that's nearing expiration.
- **Revoke token**: Immediately expire the token. After you revoke it, the token is no longer usable. This option is useful if you:

    - Accidentally share the token with an unauthorized party.
    - Complete all enrollments and no longer need the token.
- **Export token**: Export the JSON content of the token. You can use this option to get the JSON content required for Google Zero Touch or Knox Mobile Enrollment configuration.

When applied, these actions don't have any effect on devices that are already enrolled.

## Reporting

Note

If you choose to apply a custom naming template while using staging, there are some reporting details to be aware about. During staging, the device name appears with a *Staging\_* prefix and then your custom naming template. The name also has placeholder values for any user-affiliated variables. After the end user signs in to the Microsoft Intune app, the staging prefix goes away and the real user-affiliated values start appearing in the device name.

For example, during device staging the device name appears as **Staging\_Store52\_User2345\_3408**, where the staging prefix is present and the user-affiliated variables are placeholders. After the user signs in to the app, the device name appears as **Store52\_Eric\_3408**.

To view all devices with a staging token, go to **Devices** &gt; **All devices**.

Devices set up via staging remain in stage 2 until the end user signs in with their work or school account. These devices appear in the report with a *staging* prefix.

- Naming convention: *Staging\_serialnumber\_enrollmentmode\_MM/DD/YY\_H.MM*
- Example: *Staging\_ XX1234\_AnroidEnterprise\_06/22/2024\_ 4.20 AM*

After end users complete enrollment, the *username* replaces the *staging* prefix in the report.

- Naming convention: *Username\_enrollmentmode\_MM/DD/YY\_H.MM*
- Example: *john@contoso.com\_ AnroidEnterprise\_06/22/2024\_ 4.20 AM*