---
layout: Conceptual
title: Android Enterprise email settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android-enterprise
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
description: Create device configuration email profiles that use Exchange servers, and retrieve attributes from Microsoft Entra ID. Enable SSL or SMIME, authenticate users with certificates or username/password, and synchronize email and schedules on Android Enterprise personally owned devices with a work profile using Microsoft Intune.
ms.date: 2026-06-23T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: sheetg
locale: en-us
document_id: 7baeb22a-11f3-74db-825e-692a10e70ede
document_version_independent_id: 7baeb22a-11f3-74db-825e-692a10e70ede
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-email-settings-android-enterprise.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-email-settings-android-enterprise
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-email-settings-android-enterprise.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 7130a1ae-8dac-8c13-99e0-b8449400a3a5
---

# Android Enterprise email settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article describes the different email settings you can control on Android Enterprise personally owned devices with a work profile. As part of your mobile device management (MDM) solution, use these settings to configure an Exchange email server, use SSL to encrypt emails, and more. The email profile uses the email app on the device, and allows users to connect to their organization email.

As an Intune administrator, you can create and assign email settings to Android Enterprise personally owned devices with a work profile. To learn more about email profiles in Intune, go to [configure email settings](configure-email).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platform:
> 
> - Android Enterprise personally owned devices with a work profile (BYOD)
> 
> 
> On Android Enterprise Fully Managed, Dedicated, and Corporate-owned Work Profiles, use [app configuration policies](../../app-management/configuration/configure-managed-android).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure this policy and start collecting inventory data from devices, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Deploy your [email app](configure-email). If your profile uses Gmail and you want to use modern authentication, you might need to deploy the Google Chrome app to the work profile.
> - Create an [Android Enterprise email device configuration profile](configure-email) &gt; **Personally-owned work profile**.
> 

## Android Enterprise

- **Email app**: Select **Gmail** or **Nine Work**. This client app connects to the email server you enter.
- **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Make sure your users have email addresses that match the attribute you select. Your options:

    - **User Principal Name**: Gets the name, like `user1` or `user1@contoso.com`.
    - **User name**: Gets only the name, like `user1`.
- **Email address attribute from Microsoft Entra ID**: This name is the email attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the email address this profile uses. Your options:

    - **User principal name**: Uses the full principal name, like `user1@contoso.com` or `user1`, as the email address.
    - **Primary SMTP address**: Uses the primary Simple Mail Transfer Protocol (SMTP) address, like `user1@contoso.com`, to sign in to Exchange.
- **Authentication method**: Select **Username and Password** or **Certificates** as the authentication method used by the email profile.

    - If you select **Certificate**, select a client [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.
- **SSL**: **Enable** uses Secure Sockets Layer (SSL) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** doesn't use SSL.
- **Amount of email to synchronize**: Select the amount of time of email you want to synchronize. Or, select **Unlimited** to synchronize all available email.
- **Content type to sync** (Nine Work only): Select the data you want to synchronize on the devices. Your options:

    - **Contacts**: **Enable** allows end users to sync contacts to their devices.
    - **Calendar**: **Enable** allows end users to sync the calendar to their devices.
    - **Tasks**: **Enable** allows end users to sync any tasks to their devices.