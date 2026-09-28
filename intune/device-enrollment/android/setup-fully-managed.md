---
layout: Conceptual
title: Set up enrollment for Android Enterprise fully managed devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-fully-managed
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
description: Set up enrollment in Intune for devices using the Android Enterprise fully managed device management solution.
ms.date: 2026-05-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilso
locale: en-us
document_id: 9843a9f2-99f9-cefd-0901-93330a4f25f1
document_version_independent_id: 9843a9f2-99f9-cefd-0901-93330a4f25f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/setup-fully-managed.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/setup-fully-managed
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/setup-fully-managed.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: dd001593-f02a-f6ee-cea7-7f9d6a0bf78c
---

# Set up enrollment for Android Enterprise fully managed devices - Microsoft Intune | Microsoft Learn

Set up the *Android Enterprise fully managed device* solution in Microsoft Intune to enroll and manage corporate-owned devices. A fully managed device is associated with a single user and is intended for work, not personal use. As an Intune admin, you can manage the whole device and enforce policy controls that aren't available with Android Enterprise work profile, such as:

- Allow app installation from Managed Google Play only.
- Block users from uninstalling managed apps.
- Prevent users from factory resetting devices.

You and your device users can initiate enrollment by entering or scanning an enrollment token during device setup. This article describes the prerequisites for enrollment and how to create enrollment profiles and tokens. At the end of this article, you can enroll devices.

## Step 1: Prerequisites

Complete these prerequisites to ensure a successful enrollment.

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Make sure Android Enterprise is supported in your region. For Android Enterprise requirements, see [Get started with Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&amp;ref_topic=6151012).

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Devices must:
> 
> - Run Android OS version 10.0 and later.
> - Run an Android build that has Google Mobile Services connectivity.
> - Have Google Mobile Services available and be able to connect to it.
> 
> 
> There's no restriction on device manufacturer/OEM if all three requirements are met. Make sure Android Enterprise is supported on devices. For more information, see:
> 
> - [Android Enterprise help - General FAQs](https://support.google.com/work/android/answer/14772109?hl=en#zippy=%2cif-my-device-is-not-android-enterprise-recommended-aer-can-i-still-use-android-enterprise)
> - [Check & fix Play Protect certification status](https://support.google.com/googleplay/answer/7165974?hl=en#zippy=%2Cdevice-isnt-certified)
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - An Intune standalone tenant, with the [mobile device management (MDM) authority set to Microsoft Intune](../../fundamentals/setup-mdm-authority).
> - [Connect your Intune tenant account to your Android Enterprise account](connect-managed-google-play).
> 

Note

The Android setup process uses a Chrome tab to authenticate device users during enrollment. If you have a Microsoft Entra Conditional Access policy with the following configurations, you must exclude the Microsoft Intune cloud app from the policy:

- *Require a device to be marked as compliant* setting is used to grant or block access.
- The policy applies to **All Cloud apps**, **Android**, and **Browsers**.

## Step 2: Create new enrollment profile

Intune automatically generates a default enrollment profile and enrollment token for fully managed devices. The default enrollment profile is named **Default Fully Managed Profile**.

To create a new enrollment profile:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Android** tab.
4. Under **Android Enterprise** &gt; **Enrollment Profiles**, choose **Corporate-owned, fully managed user devices**.
5. Select **Create policy**.
6. Enter the basics for your profile:

    - **Name**: Give the profile a name. Note the name down for later, because you need it when you set up the dynamic device group.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Token type**: Choose the type of token you want to use to enroll corporate fully managed devices. For more information, see Token types in this article. Your options:

        - **Corporate-owned, fully managed (default)**
        - **Corporate-owned, fully managed, via staging**

        Tip

        Enrollment time grouping isn't supported with the staging token. If you're configuring a profile for use with enrollment time grouping, use the corporate-owned, fully managed (default) token.
    - **Token expiration date**: Only available with the staging token. Enter the date you want the token to expire, up to 65 years in the future. Acceptable date format: `MM/DD/YYYY` or `YYYY-MM-DD` The token expires on the selected date at 12:59:59 PM in the time zone it was created.
    - **Naming Template**: The default behavior names devices using properties of the device, such as enrollment type, device ID, and time of enrollment. Example: *AndroidForWork\_01/01/2025\_12:00 PM*

        To create a custom naming template:

        1. Under **Apply device name template**, choose **Yes**.
        2. Enter the naming template you want to apply to the devices. Names can contain letters, numbers, and hyphens.

        You can use the following strings to create your naming template. Intune replaces the strings with device-specific values.

        - {{SERIAL}} for the device's serial number.
        - {{SERIALLAST4DIGITS}} for the last 4 digits of the device’s serial number.
        - {{DEVICETYPE}} for the device type. Example: *AndroidForWork*
        - {{ENROLLMENTDATETIME}} for the date and time of enrollment.
        - {{UPNPREFIX}} for the user's first name. Example: *Eric*, when device is user affiliated.
        - {{USERNAME}} for the user's username when the device is user affiliated. Example: *EricSolomon*
        - {{RAND:x}} for a random string of numbers, where *x* is between 1 and 9 and indicates the number of digits to add. Intune adds the random digits to the end of the name.

        Edits you make to the naming template only apply to new enrollments.
7. Select **Next** to continue to **Device group**.
8. Optionally, select where to group devices at enrollment time. Select **Search by group name**. Then find and select a static Microsoft Entra device group. For information about how to create a device group to use for grouping, see [Set up enrollment time grouping](../setup-time-grouping).

    Tip

    Be sure to select a device group, not a user group.
9. Select **Next** to continue to **Scope tags**.
10. Apply one or more scope tags to limit profile visibility and management to certain admin users in Intune. Scope tags are optional. For more information about how to use scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
11. Select **Next** to continue to **Review + create**.
12. Review the summary of your profile, and then select **Create** to finalize it.

To review, make changes, or delete the profile:

1. Select the profile.
2. Select **Overview** to review profile essentials and delete the profile.
3. Select **Properties** &gt; **Edit** to make changes to the profile basics or scope tags.
4. Select **Token** to retrieve, revoke, or export the token.

## Step 3: Create dynamic Microsoft Entra group

Optionally, create a dynamic Microsoft Entra group to automatically group devices based on a certain attribute or variable. In this case, we want to use the `enrollmentProfileName` property to group devices that are enrolling with the same profile.

Note

Dynamic groups based on `enrollmentProfileName` are useful when you need group membership for cross-workload scenarios (like Conditional Access or group-based licensing). If your goal is only to target Intune policies and apps to devices with specific properties, consider using [assignment filters](../../fundamentals/filters/overview) instead. Filters evaluate at check-in without depending on group membership processing.

Add these configurations to your group:

- **Group type**: Security
- **Membership type**: Dynamic Device
- Add a dynamic query with the following rule:

    - **Property**: enrollmentProfileName
    - **Operator**: Equals
    - **Value**: Enter the name of the enrollment profile you created in Step 2: Create new enrollment profile.

You can't use dynamic groups with the default enrollment profile. For more information about how to create a dynamic group with rules, see [Create a group membership rule](/en-us/azure/active-directory/enterprise-users/groups-create-rule#to-create-a-group-membership-rule).

## Step 4: Enroll devices

Note

The Microsoft Authenticator app automatically installs on fully managed devices during enrollment. This app is required for this enrollment method and cannot be uninstalled.

After you set up the enrollment profile, token, and dynamic group, you can use any of these provisioning methods to enroll devices as fully managed:

- Near Field Communication (NFC)
- Token string or QR code
- Zero-touch enrollment
- Samsung Knox Mobile Enrollment

For the next steps, including how to enroll devices with each provisioning method, see [Enroll Android Enterprise corporate-owned devices](ref-corporate-methods).

## Token types

When you create the enrollment profile in the admin center, you have to select a token type. There are two types of tokens. Each type enables a different enrollment flow.

The default token, *corporate-owned, fully managed*, enrolls devices into Microsoft Intune as standard Android Enterprise corporate fully managed devices. This token requires you to complete pre-provisioning steps before you distribute the devices. End users complete the remaining steps on the device when they sign in with their work or school account.

The device staging token, *Corporate-owned, fully managed, via staging*, enrolls devices into Microsoft Intune in a staging mode so that you or a third party vendor can complete all pre-provisioning steps. End users complete the last step of provisioning by signing in to the Microsoft Intune app with their work or school account. Devices are ready to use upon sign-in. Intune supports device staging for Android Enterprise devices running Android 10 or later.

For more information, see [Device staging overview](device-staging).

## Replace, remove, or export token

Select a token in the admin center to access these management options:

- **Replace token**: Generate a new token that's nearing expiration.
- **Revoke token**: Immediately expire the token. After you revoke it, the token is no longer usable. This option is useful if you:

    - Accidentally share the token with an unauthorized party.
    - Complete all enrollments and no longer need the token.
- **Export token**: Export the JSON content of the token. You can use this option to get the JSON content required for Google Zero Touch or Knox Mobile Enrollment configuration.

When applied, these actions don't have any effect on devices that are already enrolled.