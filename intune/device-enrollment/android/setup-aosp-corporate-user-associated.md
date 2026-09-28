---
layout: Conceptual
title: Set up Android (AOSP) device management in Intune for corporate-owned user-associated devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-user-associated
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
description: Set up Intune for corporate-owned user-associated devices built on the Android Open Source Project (AOSP) platform.
ms.date: 2025-05-15T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: jieyan
locale: en-us
document_id: c88ebe15-57bd-dc2e-1cee-355adfb5e278
document_version_independent_id: c88ebe15-57bd-dc2e-1cee-355adfb5e278
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/setup-aosp-corporate-user-associated.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/setup-aosp-corporate-user-associated
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/setup-aosp-corporate-user-associated.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 9287590d-2499-adc6-7e3a-e56348ad86b5
---

# Set up Android (AOSP) device management in Intune for corporate-owned user-associated devices - Microsoft Intune | Microsoft Learn

Set up enrollment in Intune for corporate-owned, user-associated devices built on the Android Open Source Project (AOSP) platform. Intune offers an *Android (AOSP)* device management solution for corporate-owned Android devices that are:

- Not integrated with Google Mobile Services.
- Intended to be used by a single user.
- Used exclusively for work.

This article describes how to set up Android (AOSP) device management and enroll AOSP devices for use at work.

## Prerequisites

Note

Beginning October 1st, AOSP devices must have the Microsoft Intune app, version 24.7.0 or later to sync with the Microsoft Intune service.

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - [Android (AOSP)](../../fundamentals/ref-supported-platforms#android)
> 

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> Assign valid licenses to all specialized device users. For more information, see [Microsoft Intune licensing](../../fundamentals/licensing) and [Managing specialty devices with Microsoft Intune](../../device-management/specialty-devices).

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - An active Microsoft Intune tenant.
> - [Set Microsoft Intune as the mobile device management (MDM) authority in your tenant](../../fundamentals/setup-mdm-authority). You only need to do this once, when you first set up Intune for mobile device management.
> 

## Create an enrollment profile

Create an enrollment profile to enable enrollment on devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Android** tab.
4. Under **Android Open Source Project (AOSP)**, choose **Corporate-owned, user-associated devices**.
5. Select **Create profile**.
6. Enter the basics for your profile:

    - **Name**: Give the profile a name. Note the name down for later, because you'll need it when you set up the dynamic device group.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Token expiration date**: Select the date the token expires, which can be up to 65 years in the future.
    - **SSID**: Identifies the network that the device will connect to.

        Note

        Wi-Fi details are required if the device doesn't have a button or option that lets it automatically connect to a network.
    - **Hidden network**: Choose whether this is a hidden network. By default, this setting is disabled, which means the network can broadcast its SSID.
    - **Wi-Fi type**: Select the type of authentication needed for this network.

        If you select **WEP Pre-shared key** or **WPA Pre-shared key**, also enter:

        - **Pre-shared key**: The pre-shared key that's used to authenticate with the network.
    - **For Microsoft Teams devices**: Select **Enabled** if this profile is applicable for Microsoft Teams Android devices. This setting should only be used for [Microsoft Teams Android devices](/en-us/microsoftteams/devices/teams-ip-phones). You can enable this setting in one enrollment profile per tenant.
    - **Naming Template**: The default behavior names devices using properties of the device, such as enrollment type, device ID, and time of enrollment. Example: *EricSolomon\_AndroidAOSP\_05/02/2025\_5:09 PM*

        To create a custom naming template:

        1. Under **Apply device name template**, choose **Yes**.
        2. Enter the naming template you want to apply to the devices. Names can contain letters, numbers, and hyphens.

        You can use the following strings to create your naming template. Intune replaces the strings with device-specific values.

        - {{SERIAL}} for the device's serial number.
        - {{SERIALLAST4DIGITS}} for the last 4 digits of the device's serial number.
        - {{DEVICETYPE}} for the device type, Example: *AndroidAOSP*
        - {{ENROLLMENTDATETIME}} for the date and time of enrollment.
        - {{UPNPREFIX}} for the user's first name. Example: *Eric*, when device is user affiliated.
        - {{USERNAME}} for the user's username when the device is user affiliated. Example: *Eric Solomon*
        - {{RAND:x}} for a random string of numbers, where *x* is between 1 and 9 and indicates the number of digits to add. Intune adds the random digits to the end of the name.

        Edits to the naming template only apply to new enrollments.
7. Select **Next** and optionally, select scope tags.
8. Select **Next**. Review the details of your profile and then select **Create** to save the profile.

### Access enrollment token

After you create a profile, Intune generates a token that's needed for enrollment. The token appears as a QR code. During device setup, when prompted to, scan the QR code to enroll the device in Intune.

To view the token as a QR code, select your enrollment profile from the enrollment profile list. Then select **Token**. You can also export the enrollment profile JSON file. To create a JSON file, select **Export**.

Important

- The QR code contains any credentials provided in the profile in plain text to allow the device to successfully authenticate with the network. This is required as the user can't join a network from the device.
- Consider using a staging network with limited permissions for provisioning devices and completing the enrollment process. For example, you could use an internet-connected network with limited permissions and no corporate access to do the initial setup.
- On RealWear devices, you should skip the first time setup. The Intune QR code is the only thing you need to set up the device.

### Replace a token

You can generate a new token to replace one that's nearing its expiration date. The replacement token doesn't affect devices that are already enrolled.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Android** tab.
3. In the **Android Open Source Project (AOSP)** section, choose **Corporate-owned, user-associated devices**.
4. Choose the profile that you want to work with.
5. Select **Token** &gt; **Replace token**.
6. Enter the token's new expiration date, which can be up to 65 years in the future.
7. Select **OK**.

### Revoke a token

Revoke a token to immediately expire it and make it unusable. For example, it's appropriate to revoke a token when:

- You accidentally share the token/QR code with an unauthorized party.
- You complete all enrollments and no longer need the token.

Revoking a token has no effect on devices that are already enrolled.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Android** tab.
3. In the **Android Open Source Project (AOSP)** section, choose **Corporate-owned, user-associated devices**.
4. Choose the profile that you want to work with.
5. Select **Token** &gt; **Revoke token** &gt; **Yes**.

## Create a device group

You can create *assigned device groups* or *dynamic device groups* in Intune. For more information about groups, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).

Dynamic device groups are configured to automatically add and remove devices based on a set of rules and parameters. For example, you can group devices by enrollment profile name.

Complete the following steps to create a dynamic Microsoft Entra device group for devices enrolled with an Android (AOSP) corporate-owned, user-associated enrollment profile.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Groups** &gt; **All groups** &gt; **New group**.
2. In the **Group** blade, fill out the required fields as follows:

    - **Group type**: Security
    - **Group name**: Type an intuitive name (like Factory 1 devices)
    - **Membership type**: Dynamic device
3. Choose **Add dynamic query**.
4. In the **Dynamic membership rules** blade, fill out the fields as follows:

    - **Add dynamic membership rule**: Simple rule
    - **Add devices where**: enrollmentProfileName
    - In the middle box, choose **Equals**.
    - In the last field, enter the enrollment profile name that you created earlier.

    For more information about dynamic membership rules, see [Dynamic membership rules for groups in Microsoft Entra ID](/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership).
5. Choose **Add query** &gt; **Create**.

## Enroll devices via QR code

After you set up and assign the Android (AOSP) enrollment profiles, you can enroll devices via QR code.

1. Turn on your new or factory-reset device.
2. When the device prompts you to, scan the token's QR code.

Tip

To access the token in Intune, go to **Devices** &gt; **Enrollment**. Then select the \**Android* tab &gt; **Corporate-owned, user-associated devices**. Select your enrollment profile, and then choose **Token**.

1. Step through the on-screen prompts to finish enrolling and registering the device. The following apps are automatically installed during this time and used for enrollment:

    - Microsoft Intune app
    - Intune Company Portal app
    - Microsoft Authenticator app

To use JSON to enroll devices, refer to instructions provided by the device manufacturer.

## After enrollment

### Update apps

The Microsoft Intune app automatically updates itself. When an app update becomes available, the Intune app closes and installs the update. The app must remain closed to install the update. The app also installs updates for Microsoft Authenticator and the Company Portal app.

### Manage devices remotely

The following remote actions are available for Android (AOSP) devices:

- Wipe
- Delete

You can take action on one device at a time. For more information, see [Remote Device Actions In Microsoft Intune](../../device-management/actions/).

Note

After you wipe an Android (AOSP) device, the device remains in a **Pending** state until it's fully restored to its factory default settings. Then Intune removes it from the device list. When you delete a device, the device is removed from the device list immediately, with no pending status, and the factory reset happens the next time the device checks in.

## Troubleshooting

### View app versions

Find out which version of the Intune app or Microsoft Authenticator app is installed on a device.

1. Go to **Devices** and select the device name.
2. Select **Discovered apps**.
3. Find your app and then look in the **Application Version** column for the version number.

### Troubleshooting + Support

Select **Troubleshooting + Support** in the admin center to:

- See a list of Android (AOSP) devices enrolled by a user
- Enable troubleshooting of Android (AOSP) devices the same way you can troubleshoot other user devices.

### Share app logs with Microsoft

If you experience problems with enrollment or access to work resources, you can share diagnostic logs with Microsoft in the Intune app or Company Portal app. After you submit the logs, you'll receive an incident ID to share with your Microsoft support person.

## Known limitations

The following are known limitations when working with AOSP devices in Intune:

- You can't enforce certain password types via device compliance and device restrictions profiles. Password types include:
    - Password required, no restriction
    - Alphabetic
    - Alphanumeric
    - Alphanumeric with symbols
    - Weak biometric
- Device compliance reporting isn't available for Android (AOSP).
- Android (AOSP) management isn't supported with Intune operated by 21Vianet.