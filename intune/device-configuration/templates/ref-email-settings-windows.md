---
layout: Conceptual
title: Email settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-windows
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
description: Create a device configuration email profile that that uses Exchange servers, and retrieves attributes from Microsoft Entra ID. You can also enable SSL, and synchronize email and schedules on Windows 10/11 client devices using Microsoft Intune.
ms.date: 2026-06-23T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: sheetg
locale: en-us
document_id: 91a9686d-c836-5d2d-c10d-4c56d17ca784
document_version_independent_id: 91a9686d-c836-5d2d-c10d-4c56d17ca784
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-email-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-email-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-email-settings-windows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: adf394f4-6178-8890-1a98-5be2ff855a83
---

# Email settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

In Microsoft Intune, you can create and configure an email profile to connect to an Exchange email server, choose how users authenticate, use S/MIME for encryption, and more. The email profile uses the native or built-in email app on the device, and users can connect to their organization email.

This article describes some of the settings you can configure. You can create a device configuration profile to assign or deploy these email settings to your iOS/iPadOS devices.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platform:
> 
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure this policy and start collecting inventory data from devices, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Deploy your [email app](configure-email).
> - Create a [Windows e-mail device configuration profile](configure-email).
> 

## Email settings

- **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
- **Account name**: Enter the display name for the email account. This name is shown to users on their devices. For example, enter `Contoso corporate email`.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Your options:

    - **User Principal Name**: Gets the name, such as `user1` or `user1@contoso.com`.
    - **Primary SMTP address**: Gets the name in email address format, such as `user1@contoso.com`.
    - **sAM Account Name**: Requires the domain, such as `domain\user1`. Also enter:
        - **User domain name source**: Select **Microsoft Entra ID** or **Custom**.

            When getting the attributes from Microsoft Entra ID, also enter:

            - **User domain name attribute from Microsoft Entra ID**: Choose to get the **Full domain name** or the **NetBIOS name** Microsoft Entra attribute of the user.

            When using **Custom** attributes, also enter:

            - **Custom domain name to use**: Enter a value that Intune uses for the domain name, such as `contoso.com` or `contoso`.
- **Email address attribute from Microsoft Entra ID**: Intune gets this attribute from Microsoft Entra ID. Choose how the email address for the user is generated. Make sure your users have email addresses that match the attribute you select. Your options:

    - **User principal name**: Uses the full principal name as the email address, such as `user1@contoso.com` or `user1`.
    - **Primary SMTP address**: Uses the primary SMTP address to sign in to Exchange, such as `user1@contoso.com`.

### Security

- **SSL**: **Enable** uses Secure Sockets Layer (SSL) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** doesn't require SSL.

### Synchronization

- **Amount of email to synchronize**: Select the number of days of email that you want to synchronize. When set to **Not configured** (default), Intune doesn't change or update this setting. Select **Unlimited** to synchronize all available email.
- **Sync schedule**: Select the schedule for devices to synchronize data from the Exchange server. You can also select **As Messages arrive**, which synchronizes data as soon as it arrives. Or, select **Manual** so the device user starts the synchronization.

    When set to **Not configured** (default), Intune doesn't change or update this setting.

### Content type to sync

Select the content types that you want to synchronize to devices. Your options:

- **Contacts**: **On** syncs the contacts. **Off** doesn't automatically sync the contacts. Users manually sync.
- **Calendar**: **On** syncs the calendar. **Off** doesn't automatically sync the contacts. Users manually sync.
- **Tasks**: **On** syncs the tasks. **Off** doesn't automatically sync the tasks. Users manually sync.