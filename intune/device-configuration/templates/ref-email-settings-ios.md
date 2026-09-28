---
layout: Conceptual
title: Configure Email settings for iOS/iPadOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-ios
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
description: See a list of all the email settings you can configure and add to iOS and iPadOS devices in Microsoft Intune, including using Exchange servers, and getting attributes from Microsoft Entra ID. You can also enable SSL, authenticate users with certificates or username/password, and synchronize email on iOS/iPadOS devices using device configuration profiles in Microsoft Intune.
ms.date: 2026-06-23T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: beflamm, sheetg
locale: en-us
document_id: ad5c5fa6-f2f5-e336-714e-86ade8ec6b2e
document_version_independent_id: ad5c5fa6-f2f5-e336-714e-86ade8ec6b2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-email-settings-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-email-settings-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-email-settings-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 2f9a7c51-2faf-9dc7-9291-9112f403bbaf
---

# Configure Email settings for iOS/iPadOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

In Microsoft Intune, you can create and configure an email profile to connect to an Exchange email server, choose how users authenticate, use S/MIME for encryption, and more. The email profile uses the native or built-in email app on the device, and users can connect to their organization email.

This article describes all the email settings available for devices running iOS/iPadOS. You can create a device configuration profile to push or deploy these email settings to your iOS/iPadOS devices.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platform:
> 
> - iOS/iPadOS, all enrollment types. For more information about the enrollment types, see [iOS/iPadOS enrollment](../../device-enrollment/apple/guide-ios-ipados).
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
> - Create an [iOS/iPadOS e-mail device configuration profile](configure-email).
> 
> 
> These settings use the [Apple ExchangeActiveSync payload](https://developer.apple.com/documentation/devicemanagement/exchangeactivesync) (opens Apple's web site).

## Exchange ActiveSync account settings

- **Email server**: Enter the host name of your Exchange server.
- **Account name**: Enter the display name for the email account. This name is shown to users on their devices.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Your options:

    - **User Principal Name**: Gets the name, like `user1` or `user1@contoso.com`.
    - **Primary SMTP address**: Gets the Simple Mail Transfer Protocol (SMTP) name in email address format, like `user1@contoso.com`.
    - **sAM Account Name**: Requires the domain, like `domain\user1`. Also enter:
        - **User domain name source**: Select **Microsoft Entra ID** or **Custom**:
            - **Microsoft Entra ID**: Get the attributes from Microsoft Entra ID. Also enter:

                - **User domain name attribute from Microsoft Entra ID**: Choose to get the **Full domain name** (`contoso.com`) or the **NetBIOS name** (`contoso`) attribute of the user.
            - **Custom**: Get the attributes from a custom domain name. Also enter:

                - **Custom domain name to use**: Enter a value that Intune uses for the domain name, like `contoso.com` or `contoso`.
- **Email address attribute from Microsoft Entra ID**: Choose how the email address for the user is generated. Make sure your users have email addresses that match the attribute you select. Your options:

    - **User principal name**: Use the full principal name as the email address, like `user1@contoso.com` or `user1`.
    - **Primary SMTP address**: Use the primary SMTP address that signs in to Exchange, like `user1@contoso.com`.
- **Authentication method**: Choose how users to authenticate to the email server. Your options:

    - **Certificate**: Select a client [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile you previously created to authenticate the Exchange connection. This option provides the most secure and better experience for your users.
    - **Username and password**: Users are prompted to enter their user name and password.
    - **Derived credential**: Use a certificate that's derived from a user's smart card. For more information, go to [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).

    Note

    Azure multifactor authentication isn't supported.
- **SSL**: **Enable** uses Secure Sockets Layer (SSL) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** uses Secure Sockets Layer (SSL) communication.
- **OAuth**: **Enable** uses Open Authorization (OAuth) communication when sending emails, receiving emails, and communicating with Exchange. If your OAuth server uses certificate authentication, choose **Certificate** as the **Authentication method**, and include the certificate with the profile. Otherwise, choose **Username and password** as the **Authentication method**. When using OAuth, be sure to:

    - Confirm your email solution supports OAuth before targeting this profile to your users. Microsoft 365 Exchange Online supports OAuth. On-premises Exchange and other partner or non-Microsoft solutions might not support OAuth. On-premises Exchange can be configured for Modern Authentication. For more information, go to [Hybrid modern authentication overview and prerequisites for on-premises Skype for Business and Exchange servers](/en-us/office365/enterprise/hybrid-modern-auth-overview).

        If the email profile uses Oauth, and the email service doesn't support it, then the **Re-Enter password** option appears broken. For example, nothing happens when the user selects **Re-Enter password** in Apple's device settings.
    - When OAuth is enabled, end users have a different "Modern Authentication" email sign-in experience that supports multifactor authentication (MFA).
    - Some organizations disable the end user's ability to do [self-service application access](/en-us/azure/active-directory/manage-apps/manage-self-service-access). In this scenario, the Modern Authentication sign-in can fail until an admin creates the "iOS Accounts" enterprise app, and grant users access to the app in Microsoft Entra ID.

        The default action is to add an application using the [Application Access Panel](/en-us/azure/active-directory/user-help/active-directory-saas-access-panel-introduction)**Add App** feature **without business approval**. For more information, go to [assign users to applications](/en-us/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

    Note

    When you enable OAuth, the following happens:

    1. Devices that are already targeted are issued a new profile.
    2. End users are prompted to enter their credentials again.

## Exchange ActiveSync profile configuration

When you configure these settings, you deploy a new profile to the device, even if you're updating an existing email profile to include these settings. Users are prompted to enter their Exchange ActiveSync account password. These settings take effect when the password is entered.

- **Exchange data to sync**: When using Exchange ActiveSync, choose the Exchange services that are synced on the device: Calendar, Contacts, Reminders, Notes, and Email. Your options:

    - **All data** (default): Sync is enabled for all services.
    - **Email only**: Sync is enabled for Email only. Sync is disabled for the other services.
    - **Calendar only**: Sync is enabled for Calendar only. Sync is disabled for the other services.
    - **Calendar and Contacts only**: Sync is enabled for Calendar and Contacts only. Sync is disabled for the other services.
    - **Contacts only**: Sync is enabled for Contacts only. Sync is disabled for the other services.

    This feature applies to:

    - iOS 13.0 and newer
    - iPadOS 13.0 and newer
- **Allow users to change sync settings**: Choose if users can change the Exchange ActiveSync settings for the Exchange services on the device: Calendar, Contacts, Reminders, Notes, and Email. Your options:

    - **Yes** (default): Users can change the sync behavior of all services. Choosing **Yes** allows changes to *all* services.
    - **No**: Users can't change the sync settings of all the services. Choosing **No** blocks changes to *all* services.

    Tip

    If you configured the **Exchange data to sync** setting to sync only some services, select **No** for this setting. Choosing **No** prevents users from changing the Exchange service that's synced.

    This feature applies to:

    - iOS 13.0 and newer
    - iPadOS 13.0 and newer

## Exchange ActiveSync email settings

- **S/MIME**: S/MIME uses email certificates that provide extra security to your email communications by signing, encrypting, and decrypting. When you use S/MIME with an email message, you confirm the authenticity of the sender, and the integrity and confidentiality of the message.

    Your options:

    - **Disable S/MIME** (default): Doesn't use an S/MIME email certificate to sign, encrypt, or decrypt emails.
    - **Enable S/MIME**: Allows users to sign and/or encrypt email in the iOS/iPadOS native mail application. Also enter:

        - **S/MIME signing enabled**: **Disable** (default) doesn't allow users to digitally sign the message. **Enable** allows users to digitally sign outgoing email for the account you entered. Signing helps users who receive messages be certain that the message came from the specific sender, and not from someone pretending to be the sender.

            - **Allow user to change setting**: **Enable** allows users to change the signing options. **Disable** (default) prevents users from changing the signing, and forces users to use the signing you configured.
            - **Signing certificate type**: Your options:

                - **Not configured**: Intune doesn't update or change this setting.
                - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
                - **Derived credential**: Use a certificate that's derived from a user's smart card. For more information, go to [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).
                - **Certificates**: Select an existing [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile that signs email messages.
            - **Allow user to change setting**: **Enable** allows users to change the signing certificate. **Disable** (default) prevents users from changing the signing certificate, and forces users to use the certificate you configured.

                This feature applies to:

                - iOS 12 and newer
                - iPadOS 12 and newer
        - **Encrypt by default**: **Enable** encrypts all messages as the default behavior. **Disable** (default) doesn't encrypt all messages as the default behavior.

            - **Allow user to change setting**: **Enable** allows users to change the default encryption behavior. **Disable** prevents users from changing the encryption default behavior, and forces users to use the encryption you configured.

                This feature applies to:

                - iOS 12 and newer
                - iPadOS 12 and newer
        - **Force per-message encryption**: Per-message encryption allows users to choose which emails are encrypted before being sent.

            **Enable** shows the per-message encryption option when creating a new email. Users can then choose to opt in or opt out of per-message encryption. If the **Encrypt by default** setting is also enabled, enabling per-message encryption allows users to opt out of encryption per message.

            **Disable** (default) prevents the per-message encryption option from showing. If the **Encrypt by default** setting is also disabled, enabling per-message encryption allows users to opt in to encryption per message.

            - **Encryption certificate type**: Your options:

                - **Not configured**: Intune doesn't update or change this setting.
                - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
                - **Derived credential**: Use a certificate that's derived from a user's smart card. For more information, go to [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).
                - **Certificates**: Select an existing [SCEP](../certificates/scep-profiles) or [PKCS](../certificates/pkcs-profiles) certificate profile that signs email messages.
            - **Allow user to change setting**: **Enable** allows users to change the encryption certificate. **Disable** (default) prevents users from changing the encryption certificate, and forces users to use the certificate you configured.

                This feature applies to:

                - iOS 12 and newer
                - iPadOS 12 and newer
- **Amount of email to synchronize**: Choose the number of days of email that you want to synchronize. Or select **Unlimited** to synchronize all available email.
- **Allow messages to be moved to other email accounts**: **Enable** (default) allows users to move email messages between different accounts the users configured on their devices. **Disable** prevents users from moving email messages.
- **Allow email to be sent from third-party applications**: **Enable** (default) allows users to select this profile as the default account for sending email. It allows non-Microsoft and partner applications to open email in the native email app, like attaching files to email. **Disable** prevents this feature.
- **Synchronize recently used email addresses**: **Enable** (default) allows users to synchronize the list of email addresses that are recently used on the device with the server. **Disable** prevents this feature.
- **VPN profile for per account VPN**: Starting in iOS/iPadOS 14, email traffic for the native Mail app can be routed through a VPN based on the account the user is using. When set to **None**, Intune doesn't enable per-account VPN for this e-mail profile.

    Per-app VPN connections you create are shown in this list. If you select a VPN profile from the list, any email that's sent to and from this account in the Mail app uses the VPN tunnel. The per-app VPN connection automatically turns on when users use their organization account in the Mail app.

    This feature applies to:

    - iOS 14 and newer
    - iPadOS 14 and newer