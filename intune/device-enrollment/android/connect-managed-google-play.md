---
layout: Conceptual
title: Connect Intune account to managed Google Play account - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play
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
description: Learn how to connect your Intune account to your Managed Google Play account.
ms.date: 2025-11-11T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilson
locale: en-us
document_id: 24fdd33e-4a66-6fb8-10ea-26fbeb94a00b
document_version_independent_id: 24fdd33e-4a66-6fb8-10ea-26fbeb94a00b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/connect-managed-google-play.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/connect-managed-google-play
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/connect-managed-google-play.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 2321825b-479a-a132-b490-8172b6e81a34
---

# Connect Intune account to managed Google Play account - Microsoft Intune | Microsoft Learn

To manage Intune-enrolled devices with any of the supported Android Enterprise management options, you must connect your Microsoft Intune tenant to your managed Google Play account. Available management options include:

- [Android Enterprise personally owned work profile](setup-personal-work-profile)
- [Android Enterprise corporate-owned work profile](setup-corporate-work-profile)
- [Android Enterprise fully managed](setup-fully-managed)
- [Android Enterprise dedicated devices](setup-dedicated)

This article describes how to link your accounts in the Microsoft Intune admin center. After you connect to Google Play, these common apps for Android Enterprise are added to the admin center:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Used for Android Enterprise fully managed, dedicated, and corporate-owned work profile scenarios.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Helps you sign in to your accounts if you use two-factor verification, and is also used for Android Enterprise dedicated devices that enroll with [Microsoft Entra shared device mode](/en-us/azure/active-directory/develop/msal-shared-devices).
- **[Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Used with Android Enterprise work profile scenarios on personal devices and Intune app protection policies.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - Used for multi-app kiosk mode on Android Enterprise dedicated devices. [Learn more about Managed Home Screen](https://techcommunity.microsoft.com/t5/intune-customer-success/how-to-setup-microsoft-managed-home-screen-on-dedicated-devices/ba-p/1388060).

## Before you begin

Important

As of August 2024, you can link your Microsoft Entra account to a Google account, instead of using an enterprise Gmail account. We recommend using your Microsoft Entra account to connect to Google Play. For more information about this change, see [Google blog: How we're making Android Enterprise signup and access to Google services better](https://blog.google/products/android-enterprise/android-enterprise-signup-google-services/). Current Microsoft Intune tenants who have already associated a Gmail account with Intune will continue to be supported.

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Confirm Android Enterprise availability in your country/region. For more information, see [Is Android Enterprise available in my country/region?](https://support.google.com/work/android/answer/6270910).

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> Confirm the Microsoft Entra account you want to use. This account is used to manage the Google Admin account and associated subscriptions, and will be associated with all Android Enterprise management tasks in your Microsoft Intune tenant. The account must also have a mailbox set up to complete the validation process required by Google.

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To connect your Intune tenant to managed Google Play, sign in with an account that has the **Intune Administrator** role, or a custom Intune role with organization *read* and *update* permissions.

## Connect accounts

Tip

Due to the interaction between Google and Microsoft domains, you might need to adjust your browser settings to complete this process. Make sure that portal.azure.com, play.google.com, and enterprise.google.com are in the same security zone in your browser. For instructions on how to perform these configurations in your browser, see [Per-site configuration by policy](/en-us/deployedge/per-site-configuration-by-policy).

Complete these steps to enable Android Enterprise management options in Microsoft Intune.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Android** tab.
4. Under **Prerequisites**, choose **Managed Google Play**. If you're using a custom Intune role, access to this option requires organization *read* and *update* permissions.
5. Select **I agree** to grant Microsoft permission to [send user and device information to Google](../../privacy/data-sharing/ref-intune-to-google).
6. Select **Launch Google to connect now** to open the managed Google Play website. The website opens on a new tab in your browser.
7. On the Google sign-in page, confirm that the prefilled Microsoft Entra account is the account you want to associate with all Android Enterprise management tasks for this tenant.

Important

- This account is used to manage the Google Admin account and associated subscriptions, as appropriate. The Microsoft Entra account must have an active mailbox to complete the validation process required by Google.
- We recommend using the Microsoft Entra account you're signed in to to create the Google Admin account. After you establish the connection, you can add and remove more administrators, if needed, in the Google admin console. Google recommends having at least two owners to an enterprise for redundancy.
- If the Microsoft sign-in option is missing, you might need to connect an MX record to the domain you're using for Exchange Online. For information about how to edit your domain's DNS settings, see [Add DNS records to connect your domain](/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

1. Follow the onscreen prompts to finish creating a Google Admin account.
2. When prompted, select **Allow and create account** to allow Microsoft Intune to manage your Android Enterprise devices.

Tip

After you connect to Managed Google Play and start using Collections, Google changes the Play Store mode to Custom. If you prefer all approved apps to be automatically visible, use **Reset to Basic** in the Intune admin center. For more information, see [Play Store modes and layout reset](../../app-management/deployment/add-managed-google-play#play-store-modes-and-layout-reset).

Tip

To choose a scope tag for your managed Google Play apps, go to **Tenant administration** &gt; **Connectors and tokens** &gt; **Managed Google Play** in the Microsoft Intune admin center. Then select a scope tag to apply to all newly-approved managed Google Play apps. You must have the following permissions to interact with this area in the admin center and to remove the selected scope tag. Tenant admins, or admins who are in charge of giving admin permissions to others, can go to **Tenant Administration** &gt; **Roles** to edit permissions.

- Android Sync - Read
- Android Sync – UpdateOnBoarding

## Upgrade to a managed Google domain

If you onboarded to Microsoft Intune with a Gmail account, you can optionally upgrade your Microsoft Entra account to a managed Google domain in the Intune admin center. During this process, you link your Microsoft Entra account to Google. That way you can manage the connection between Google and Intune with your Microsoft Entra account, rather than a Gmail account.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an Intune Administrator account.
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Android** tab.
4. Under **Prerequisites**, choose **Managed Google Play**.
5. Select **Upgrade**.
6. Select **Upgrade** again to confirm that you want to upgrade your enterprise.
7. In the Google popup, follow the steps. When given the option, select **Sign in with Microsoft**.

    Tip

    If you have trouble upgrading your domain or you get an error reporting that the domain is already in use, see [Can't sign up my domain for a Google service](https://support.google.com/a/answer/80610?hl=en#zippy=%2Cthis-domain-is-already-in-use) in Google support docs.
8. Select **Upgrade**.
9. Wait for the upgrade to finish. An onscreen message appears confirming that the upgrade is done. You also receive a notification in the admin center confirming that the upgrade is complete.

    Note

    After a successful upgrade, the **Upgrade** button appears grayed out because no more upgrades are available. If the button appears grayed out and you haven't upgraded, check your RBAC permissions.

## Disconnect your Android Enterprise administrative account

You can disconnect the link between Microsoft Intune and Google in the admin center. Disconnecting the account disables Android Enterprise device management for your tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an Intune Administrator account.
2. [Retire](../../device-management/actions/retire)all of the following devices:
    - Android Enterprise personally owned work profile devices
    - Android Enterprise corporate-owned work profile devices
    - Android Enterprise fully managed
    - Android Enterprise dedicated devices
3. Go to **Devices** &gt; **Enrollment**.
4. Select the **Android** tab.
5. Under **Prerequisites**, choose **Managed Google Play**.
6. Select **Disconnect**.
7. Choose **Yes** to disconnect and unenroll all Android enterprise devices from Intune.

## Edit managed Google Play organization name

When you first create a managed Google Play account, you provide a name for your organization to Google. This name appears in the Intune admin center and can also appear on Android devices. For example, on the lock screen it could appear to users as **This device is managed by [organization name]**.

Complete the steps in this section to edit the name of your organization.

1. In the **Microsoft Intune admin center**, go to **Devices**.
2. Select **Android** &gt; **Enrollment** &gt; **Managed Google Play**.
3. Select **Change organization name**. Enter the new name.

    - Names must be 2–50 characters long.
    - These characters are allowed:

        - Letters: `A–Z` and `a–z`, including accented characters such as `á`, `ñ`, and `ü`
        - Numbers: `0–9`
        - `Spaces`
        - `. , ' - & ( )`
    - These special symbols aren't allowed: `@ # $ % ^ * + = | \ / < > { } [ ]`
4. Select **Change**.