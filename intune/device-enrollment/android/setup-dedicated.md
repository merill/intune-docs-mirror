---
layout: Conceptual
title: Set up Intune enrollment for Android Enterprise dedicated devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-dedicated
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
description: Configure enrollment in Microsoft Intune for Android Enterprise dedicated devices.
ms.date: 2025-05-08T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilso
locale: en-us
document_id: 6d0395d4-4f72-5be8-34d4-718096fe4301
document_version_independent_id: 6d0395d4-4f72-5be8-34d4-718096fe4301
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/setup-dedicated.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/setup-dedicated
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/setup-dedicated.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: cc771785-c44f-cd0f-d3bc-a74402fa6b9f
---

# Set up Intune enrollment for Android Enterprise dedicated devices - Microsoft Intune | Microsoft Learn

Use the Android Enterprise dedicated devices solution with Microsoft Intune to set up corporate-owned, single-use kiosk-style devices for frontline workers. These devices are used for a single purpose, such as digital signage, ticket printing, or inventory management. As an administrator, you can lock down the usage of a device to a single app, or a limited set of apps, inclusive of web apps. Users are prevented from adding other apps or taking actions on the device unless explicitly approved by you.

Devices intended for dedicated use can be enrolled in Microsoft Intune in two ways:

- As a standard Android Enterprise dedicated device. These devices are enrolled into Intune without a user account and aren't associated with a user. These devices aren't intended for personal apps, or apps such as Microsoft Outlook or Google Mail that require user-specific account data.
- As a standard Android Enterprise dedicated device that's automatically set up with Microsoft Authenticator and configured for [Microsoft Entra shared device mode](/en-us/azure/active-directory/develop/msal-shared-devices) during enrollment. These devices are enrolled in Intune without a user account and aren't associated with a user. These devices are intended for use with apps that integrate with Microsoft Entra shared device mode, and allow for single sign-in and sign-out between users across participating apps.

This article describes how to set up and configure Microsoft Intune to enroll dedicated devices. For more information about Android Enterprise management solutions, see [Get started with Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&amp;ref_topic=6151012)(opens Android Enterprise Help Center).

## Device requirements

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Confirm Android Enterprise availability in your country/region. For more information, see [Is Android Enterprise available in my country/region?](https://support.google.com/work/android/answer/6270910).

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Devices must have:
> 
> - Android OS version 8.0 or later.
> - A distribution of Android that has Google Mobile Services (GMS) connectivity. Devices must have GMS available and must be able to connect to GMS.
> - Support for Android Enterprise. For more information about requirements and support, see:
>     - [Android Enterprise help - General FAQs](https://support.google.com/work/android/answer/14772109?hl=en#zippy=%2cif-my-device-is-not-android-enterprise-recommended-aer-can-i-still-use-android-enterprise)
>     - [Check & fix Play Protect certification status](https://support.google.com/googleplay/answer/7165974?hl=en#zippy=%2Cdevice-isnt-certified)
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - [Set the mobile device management (MDM) authority to Microsoft Intune](../../fundamentals/setup-mdm-authority). You only need to do this once, when you're first setting up Intune for mobile device management.
> - [Connect your Intune tenant account to your Managed Google Play account](connect-managed-google-play).
> 

## Set up Android Enterprise dedicated device management

To set up Android Enterprise dedicated device management, follow these steps:

1. To prepare to manage mobile devices, you must [set the mobile device management (MDM) authority to **Microsoft Intune**](../../fundamentals/setup-mdm-authority) for instructions. You set this item only once, when you're first setting up Intune for mobile device management.
2. [Connect your Intune tenant account to your Managed Google Play account](connect-managed-google-play).
3. Create an enrollment profile.
4. Create a device group.
5. Enroll the dedicated devices.

### Create an enrollment profile

Note

After a token expires, the profile associated with it disappears from view under Android enrollment &gt; **Enrollment Profiles** &gt; **Corporate-owned dedicated devices**. To see all profiles associated with both active and inactive tokens, choose **Filter**. Then select the checkboxes for **Active** and **Inactive** policy states.

You must create an enrollment profile so that you can enroll your dedicated devices. When the profile is created, it provides you with an enrollment token in the form of a string and QR code.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**, and then under **Device onboarding** select **Enrollment**.
3. Select the **Android** tab.
4. In the **Enrollment Profiles** section, choose **Corporate-owned dedicated devices**.
5. Select **Create profile**.
6. Enter the basics for your profile:

    - **Name**: Give your profile a name so you can easily identify it later.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Token type**: Choose the type of token you want to use to enroll dedicated devices.

        - **Corporate-owned dedicated device (default)**: This token enrolls devices as a standard Android Enterprise dedicated device. These devices require no user credentials at any point. This is the default token type that dedicated devices will enroll with unless updated by Admin at time of token creation.
        - **Corporate-owned dedicated device with Microsoft Entra ID shared mode**: This token enrolls devices as a standard Android Enterprise dedicated device and, during enrollment, deploys Microsoft's Authenticator app configured into Microsoft Entra shared device mode. With this option, users can achieve single sign-in and single sign-out across apps on the device that are integrated with the Microsoft Entra Microsoft Authentication Library and global sign-in/sign-out calls.
    - **Token expiration date**: Enter the date you want the token to expire, up to 65 years in the future. The token expires on the selected date at 12:59:59 PM in the time zone it was created. Acceptable date format: `MM/DD/YYYY` or `YYYY-MM-DD`
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
    - **Token expiration date**: Enter the date you want the token to expire, up to 65 years in the future. The token expires on the selected date at 12:59:59 PM in the time zone it was created. Acceptable date format: `MM/DD/YYYY` or `YYYY-MM-DD`
7. Select **Next** to continue to **Device group**.
8. Optionally, select where to group devices at enrollment time. Select **Search by group name**. Then find and select a static Microsoft Entra device group. For information about how to create a device group to use for grouping, see [Set up enrollment time grouping](../setup-time-grouping).

    Tip

    Be sure to select a device group, not a user group.
9. Select **Next** to continue to **Scope tags**.
10. Optionally, apply one or more scope tags to limit profile visibility and management to certain admin users in Intune. For more information about how to use scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
11. Select **Next** to continue to **Review + create**.
12. Review your choices, and then select **Create** to finish creating the profile.

### Access enrollment token

Access the enrollment token in the admin center.

1. Go to **Devices** &gt; **Enrollment**.
2. Select the **Android** tab.
3. In the **Enrollment Profiles** section, choose **Corporate-owned dedicated devices**.
4. From the list, select your enrollment profile.
5. Select **Token**.

The token appears as a 20-digit string and a QR code. Use this token to enroll devices via the mechanisms described in [Enroll dedicated, fully managed, or corporate-owned work profile devices](ref-corporate-methods). At the time of enrollment, the device user is prompted for the enrollment token. You can provide the string or QR, as long as it's supported by the Android OS and version of the enrolling device.

### Replace, remove, or export token

Select a token to access these options:

- **Replace token**: Generate a new token that's nearing expiration.
- **Revoke token**: Immediately expire the token. Once revoked, the token is no longer usable. This option is useful if you:
    - Accidentally share the token with an unauthorized party.
    - Complete all enrollments and no longer need the token.
- **Export token**: Export the JSON content of the token. This option is useful for obtaining the JSON content that's needed to configure [Google Zero Touch](ref-corporate-methods#enroll-by-using-google-zero-touch) or [Knox Mobile Enrollment](setup-samsung-knox-mobile).

When applied, these actions don't have any effect on devices that are already enrolled.

### Create a device group

You can target apps and policies to either assigned or dynamic device groups. You can configure dynamic Microsoft Entra device groups to automatically populate devices that are enrolled with a particular enrollment profile by following these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Groups** &gt; **All groups** &gt; **New group**.
2. Complete all required fields as follows:

    - **Group type**: Security
    - **Group name**: Type an intuitive name, like *Factory 1 devices*
    - **Membership type**: Dynamic Device
3. Choose **Add dynamic query**.
4. On the Dynamic membership rules page, complete all fields as follows:

    - **Property**: enrollmentProfileName
    - **Operator**: Equals
    - **Value**: Enter the enrollment profile name that you created earlier.

    For more information about dynamic membership rules, see [Dynamic membership rules for groups in Microsoft Entra ID](/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership).
5. Choose **Save** to finalize the rule.

## Enroll the dedicated devices

You can now [enroll your dedicated devices](ref-corporate-methods).

Note

The Microsoft Intune app will be automatically installed during enrollment of a dedicated device. This app is required for enrollment and cannot be uninstalled. Microsoft Authenticator and Company Portal will be automatically installed during enrollment of a dedicated device when using the token type **Corporate-owned dedicated device with Microsoft Entra ID shared mode**. These apps are required for this enrollment method and cannot be uninstalled.

## Managing apps on Android Enterprise dedicated devices

Only apps that have assignment type [set to Required](../../app-management/deployment/assign-groups#assign-an-app) can be installed on Android Enterprise dedicated devices. Apps are installed from the Managed Google Play store in the same manner as Android Enterprise personal and corporate owned work profile devices.

Apps are automatically updated on managed devices when the app developer publishes an update to Google Play.

To remove an app from Android Enterprise dedicated devices, you can do either of the following:

- Delete the required app deployment.
- Create an uninstall deployment for the app.