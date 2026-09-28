---
layout: Conceptual
title: Android DA email settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Create device configuration email profiles that use Exchange servers, and retrieve attributes from Microsoft Entra ID. Enable SSL or SMIME, authenticate users with certificates or username/password, and synchronize email and schedules on Android device administrator Samsung Knox devices using Microsoft Intune.
ms.date: 2025-06-09T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: sheetg
locale: en-us
document_id: 4ca30465-056f-bf08-9496-d2c5227a07df
document_version_independent_id: 4ca30465-056f-bf08-9496-d2c5227a07df
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-email-settings-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-email-settings-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-email-settings-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: b3119cd9-1a08-bf4d-b4d8-36fd3d0ae507
---

# Android DA email settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article describes the different email settings you can control on Android device administrator Samsung Knox devices in Intune. As part of your mobile device management (MDM) solution, use these settings to configure an Exchange email server, use SSL to encrypt emails, and more. The email profile uses the native or built-in email app on the device, and allows users to connect to their organization email.

This feature applies to:

- Android device administrator (DA)

As an Intune administrator, you can create and assign email settings to Android Samsung Knox Standard devices. To learn more about email profiles in Intune, go to [configure email settings](configure-email).

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- Create an [Android device administrator Email device configuration profile](configure-email).

## Android (Samsung Knox)

- **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
- **Account name**: Enter the display name for the email account. This name is shown to users on their devices.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Your options:

    - **User principal name**: Gets the name, like `user1` or `user1@contoso.com`.
    - **User name**: Gets only the name, like `user1`.
    - **sAM Account Name**: Requires the domain, like `domain\user1`. sAM account name is only used with Android devices. Also enter:
        - **User domain name source**: Select **Microsoft Entra ID** or **Custom**.

            When choosing to get the attributes from Microsoft Entra ID, enter:

            - **User domain name attribute from Microsoft Entra ID**: Select to get the **Full domain name** or the **NetBIOS name** attribute of the user.

            When choosing to use **Custom** attributes, enter:

            - **Custom domain name to use**: Enter a value that Intune uses for the domain name, like `contoso.com` or `contoso`.
- **Email address attribute from Microsoft Entra ID**: This name is the email attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the email address that this profile uses. Make sure your users have email addresses that match the attribute you select. Your options:

    - **User principal name**: Uses the full principal name, like `user1@contoso.com` or `user1`, as the email address.
    - **Primary SMTP address**: Uses the primary Simple Mail Transfer Protocol (SMTP) address, like `user1@contoso.com`, to sign in to Exchange.
- **Authentication method**: Select **Username and Password** or **Certificate** as the authentication method used by the email profile.

    - If you select **Certificate**, select a client [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.

### Security settings

- **SSL**: **Enable** uses Secure Sockets Layer (SSL) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** does use SSL.
- **S/MIME**: **Disable S/MIME** (default): Doesn't use an S/MIME email certificate to sign, encrypt, or decrypt emails. **Enable S/MIME**sends outgoing email using S/MIME encryption. Also enter:
    - Select a client [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.

### Synchronization settings

- **Amount of email to synchronize**: Select the number of days of email that you want to synchronize, or select **Unlimited** to synchronize all available email.
- **Sync schedule**: Select the schedule for devices to synchronize data from the Exchange server. You can also select **As Messages arrive**, which synchronizes data when it arrives, or **Manual**, where the user of the device must initiate the synchronization.

### Content type to sync

Select the content types that you want to synchronize on the devices.

**Not configured** disables the setting. When set to **Not configured**, if an end user enables synchronization on the device, synchronization is disabled again when the device syncs with Intune, as the policy is reinforced.

- **Contacts**: **Enable** allows end users to sync contacts to their devices.
- **Calendar**: **Enable** allows end users to sync the calendar to their devices.
- **Tasks**: **Enable** allows end users to sync any tasks to their devices.