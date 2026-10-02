---
layout: Conceptual
title: Enroll Android Enterprise dedicated, fully managed, or corporate-owned work profile devices in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/ref-corporate-methods
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
description: Learn how to enroll Android Enterprise dedicated, fully managed, or corporate-owned work profile devices in Intune.
ms.date: 2026-10-02T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilson
locale: en-us
document_id: 12447c66-5de2-4c43-99ca-d9184616f045
document_version_independent_id: 12447c66-5de2-4c43-99ca-d9184616f045
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/ref-corporate-methods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/ref-corporate-methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/ref-corporate-methods.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 76328f03-d29b-dbae-5a03-815083823d68
---

# Enroll Android Enterprise dedicated, fully managed, or corporate-owned work profile devices in Intune - Microsoft Intune | Microsoft Learn

Important

Device users shouldn't restart devices until enrollment is complete. If device users setting up fully managed devices or corporate-owned devices with a work profile restart their devices in the middle of enrollment, their devices may not be able to register with Microsoft Intune. Devices that restarted may appear to be enrolled but they won't be protected by your Intune policies.

After you've set up your Android Enterprise [dedicated devices](setup-dedicated), [fully managed devices](setup-fully-managed), or [corporate-owned work profile devices](setup-corporate-work-profile) in Intune, you can enroll the devices. You have several options for how to enroll these devices: QR code, Google Zero Touch, Knox Mobile Enrollment, Near Field Communication (NFC), or token entry.

Note

If you have a Microsoft Entra Conditional Access policy defined that uses the *require a device to be marked as compliant* Grant control or a Block policy and applies to **All Cloud apps**, **Android**, and **Browsers**, you must exclude the **Microsoft Intune** cloud app from this policy. This is because the Android setup process uses a Chrome tab to authenticate your users during enrollment. For more information, see [Microsoft Entra Conditional Access documentation](/en-us/azure/active-directory/conditional-access/).

*Factory reset protection* helps prevent unauthorized access to your device after it's been factory reset. If the device is reset without your permission, in some situations, only the Google email addresses you enter can unlock the device. When the **Factory reset protection emails** setting is configured, there is different factory reset protection behavior:

| Enrollment method | Settings &gt; Factory data reset | Settings &gt; Recovery/bootloader | Intune[wipe](../../device-management/actions/wipe) |
| --- | --- | --- | --- |
| **Corporate-owned devices with work profile** (COPE) | ✅ factory reset protection | ✅ factory reset protection | ❌ no factory reset protection |
| **Fully managed** (COBO) | ❌ no factory reset protection | ✅ factory reset protection | ❌ no factory reset protection |
| **Dedicated** (COSU) | ❌ no factory reset protection | ✅ factory reset protection | ❌ no factory reset protection |

For corporate-owned devices with a work profile, a Settings reset doesn't enforce FRP when **Factory reset protection emails** is **Not configured**.

For corporate owned devices with a work profile running Android 15, when **Factory reset protection emails** is configured with a Google account email address, you will need to re-enter the Google account associated with the configuration after a reset done via the Settings app. It's important to plan your reprovisioning workflow (such as applying an Intune wipe or resetting via the Settings app) accordingly so that you can provide the required credentials if needed. For background and guidance, see [Factory reset protection (FRP) enforcement behavior for Android Enterprise](/en-us/troubleshoot/mem/intune/device-configuration/factory-reset-protection-emails-not-enforced).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms on [supported Android OS versions](../../fundamentals/ref-supported-platforms#android):
> 
> - Android Enterprise corporate owned fully managed devices (COBO)
> - Android Enterprise corporate owned dedicated devices (COSU)
> - Android Enterprise corporate-owned devices with a work profile (COPE)
> 

## Enroll by using a QR code

Intune admins can scan the QR code directly from the enrollment profile to enroll a device. We recommend this enrollment method for most customer scenarios.

1. After you wipe the device, tap the first screen you see repeatedly to launch the QR reader.
2. If prompted to, install a QR reader on your device. Devices running Android 9.0 and later are preinstalled with a QR reader.
3. Scan the enrollment profile QR code, and then follow the on-screen prompts to complete enrollment. 
    Tip

    Browser zoom settings may prevent your device from scanning the QR code. Zoom in and try again if your device has difficulty scanning the code.

## Enroll by using Google Zero Touch

Important

Devices must be purchased from an authorized zero-touch reseller and support zero-touch enrollment. For more information, such as prerequisites, where to purchase devices, and how to associate a Google Account with your corporate email, see [Zero-touch enrollment for IT admins](https://support.google.com/work/android/answer/7514005) (opens Android Enterprise Help docs).

This method utilizes zero-touch enrollment and the Google zero-touch enrollment portal to provision and enroll company-owned devices. Provisioning begins right out of the box when users turn their devices on. This section describes how to:

- Create a zero-touch configuration with provisioning details in the Microsoft Intune admin center.
- Create a zero-touch configuration with provisioning details in the zero-touch enrollment portal.

### Create zero-touch configuration in admin center

The zero-touch iframe gives you access to the zero-touch enrollment portal and zero-touch configurations in the Microsoft Intune admin center.

To enable the iframe, you must first add the *update app sync* permission and enable enrollment for corporate-owned, fully managed devices. Once you enable the iframe, you can:

- Link your zero-touch account to Intune
- Add support information
- Configure zero-touch enabled devices
- Customize provisioning extras

Complete the steps in this section to enable the iframe. To create configurations in the zero-touch enrollment portal instead, skip to [Create configuration in zero-touch enrollment portal](ref-corporate-methods#create-configuration-in-zero-touch-enrollment-portal).

#### Step 1: Add required permission

Add the *update app sync* permission.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) admin.
2. Select **Tenant administration** &gt; **Roles**.
3. Select your role from the list.
4. Select **Properties**.
5. Go to **Permissions** and then select **Edit**.
6. Select **Android Enterprise**.
7. Next to **Update app sync**, select **Yes**.
8. Select **Review + save** to review your changes.
9. Select **Save**.

#### Step 2: Link zero-touch account to Intune

Link a zero-touch account with your Microsoft Intune account.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **By platform** &gt; **Android**.
2. Select **Device onboarding** &gt; **Enrollment**.
3. Under **Bulk enrollment methods**, choose **Zero-touch enrollment**.
4. The iframe opens. Select **Next** to begin setup.
5. Sign in with the Google account you provided to your reseller.
6. Select the zero-touch account you want to link, and then select **Link**.
7. A default configuration is created. A screen appears with basic information about the configuration. Intune will automatically apply the default configuration to any zero-touch enabled device that's without an existing configuration.

Caution

The token used for the default configuration is meant for a fully managed device. Once you link your account, the default zero-touch configuration created in Intune overrules the default configuration profile set in the zero-touch enrollment portal. If you want to create a zero-touch configuration for a corporate-owned work profile device or a dedicated device, don't link your account to Intune. Instead, select **View devices in the zero-touch portal**. Then continue to [Create configuration in zero-touch enrollment portal](ref-corporate-methods#create-configuration-in-zero-touch-enrollment-portal) in this article for next steps.
8. Select **Next** to continue.
9. Add support information to assist device users during setup.
10. Select **Save**.

Once your account is linked with Intune, the default configuration is applied to zero-touch enabled devices that don't already have a configuration, and to future devices added by a reseller. You can view existing zero-touch configurations, edit support information, unlink the account, and link other accounts in the admin center.

### Create configuration in zero-touch enrollment portal

Add a zero-touch configuration in the [zero-touch enrollment portal](https://enterprise.google.com/android/zero-touch/customers). You can use the portal by itself to manage configurations, or you can use it in combination with the zero-touch iframe. The portal supports configurations for fully managed and dedicated devices, and corporate-owned devices with a work profile.

1. Sign in to the zero-touch enrollment portal with your Google account.
2. Select the option to add a new configuration.
3. Fill out the information in the configuration panel.
4. Select **Microsoft Intune** as the EMM DPC app.
5. Copy the following JSON text into the DPC extras field. Replace `YourEnrollmentToken` with the enrollment token you created as part of your enrollment profile. Be sure to surround the enrollment token with double quotes.

    ```json
    {
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver",
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg",
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup",
    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": {
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken"
    }
    }
    
    ```
6. Enter your organization's name and support information, which is shown on screen while users set up their devices.

For more information about how to assign a default configuration or apply a configuration in the zero-touch portal, see [Zero-touch enrollment for IT admins](https://support.google.com/work/android/answer/7514005) (opens Android Enterprise Help docs).

## Enroll by using Knox Mobile Enrollment

To use Samsung Knox Mobile Enrollment, the device must be running [supported Samsung Knox versions](../../fundamentals/ref-supported-platforms#android). For more information, learn [how to automatically enroll your devices with Knox Mobile Enrollment](setup-samsung-knox-mobile).

## Enroll by using Near Field Communication (NFC)

Create a specially formatted NFC tag to provision NFC-supported devices. You can use your own app or any NFC tag-creation tool. For more information, see [C-based Android Enterprise device enrollment with Microsoft Intune](/en-us/archive/blogs/cbernier/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune) and [Google's Android Management API documentation](https://developers.google.com/android/management/provision-device#nfc_method).

Note

Not supported on Android Enterprise corporate-owned devices with a work profile (COPE) running Android version 11.0. For more information, see the [Google developer docs](https://developers.google.com/android/management/provision-device#nfc_method).

## Enroll by using a token

We recommend this method for new or factory-reset devices, in scenarios where the QR code or NFC method aren't available. It requires the person provisioning the device to type in the enrollment token string (example: `12345`) that they're provided. When you're ready for enrollment, share the token directly with targeted users or post it to your organization's support site for easy retrieval. The token works for all Intune-licensed users and doesn't expire.

Note

Not supported on Android Enterprise corporate-owned devices with a work profile (COPE) running Android version 11.0.

You can use this method in conjunction with the Microsoft Intune DPC identifier to set up fully managed devices.

1. Turn on the device.
2. On the **Welcome** screen, select your language.
3. Connect to your wireless network, and then choose **NEXT**.
4. Accept the Google Terms and conditions, and then choose **NEXT**.
5. On the Google sign-in screen, enter **afw#setup** instead of a Gmail account. This value is the DPC identifier for Microsoft Intune. Choose **NEXT**.
6. Choose **INSTALL** for the Android Device Policy app.
7. Continue to install the policy. Some devices may require additional terms acceptance.
8. On the **Enroll this device** screen, allow your device to scan the QR code. Or, enter the token manually.
9. Follow the on-screen prompts to complete enrollment.

For more information about provisioning devices with the DPC identifier method, see the [Google developer docs](https://developers.google.com/android/management/provision-device#company-owned_devices_for_work_and_personal_use:%7E:text=Note%3A%20DPC%20identifier%20method%20only%20supports%20full%20device%20management%20provisioning%20and%20cannot%20be%20used%20for%20corporate%2Downed%2C%20personally%20enabled,%28COPE%29%20provisioning%20on%20Android%2011%20devices.,-Company%2Downed).