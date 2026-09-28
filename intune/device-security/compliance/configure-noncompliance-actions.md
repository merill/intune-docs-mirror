---
layout: Conceptual
title: Configure compliance policies with actions for noncompliance in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-noncompliance-actions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-certificates
ms.subservice: protect
description: Configure your compliance policies with one or more actions for noncompliance to protect devices and your organization from unprotected devices. Actions can remotely lock devices, send email or notifications to device users, and more.
ms.date: 2024-01-23T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: ilwu
locale: en-us
document_id: 2882244c-7637-56ad-fc42-5df536e62f24
document_version_independent_id: 2882244c-7637-56ad-fc42-5df536e62f24
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/configure-noncompliance-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/configure-noncompliance-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/configure-noncompliance-actions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 4a7cf0f6-742c-7e45-4508-54e3bc85387c
---

# Configure compliance policies with actions for noncompliance in Microsoft Intune - Microsoft Intune | Microsoft Learn

Compliance policies can include *actions for noncompliance*, which are steps the policy takes on a schedule when it detects a device isn't meeting your security requirements. For example, a policy can remotely lock a noncompliant device to help protect it, or send a notification to users so they can understand and resolve the issue.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Overview

Each compliance policy includes **Mark device noncompliant** as a built-in default action, scheduled to trigger immediately at zero days. When Intune detects that a device isn't compliant, it marks the device noncompliant right away. Microsoft Entra [Conditional Access](/en-us/entra/identity/conditional-access/overview) can then block the device from accessing your organization's resources.

Adding more actions gives you control over what happens to noncompliant devices, and when. For example, you can give users a grace period to become compliant before blocking their access.

For each action you set, you can configure a schedule that determines when that action takes effect. The schedule is based on days after the device is marked noncompliant. You can also add the same action multiple times. If the device remains noncompliant, the action repeats at each scheduled time.

Not all actions are available for all platforms.

Note

The **Schedule (days after noncompliance)** field in the admin center accepts whole numbers and decimal values in 0.25 increments. For example, `0.25` equals 6 hours and `0.5` equals 12 hours. To use other decimal values, such as `0.33` (8 hours), configure the schedule using [Microsoft Graph](/en-us/graph/overview) instead.

## Available actions for noncompliance

The following actions are available for noncompliance:

- **Mark device non-compliant**: This built-in default action is included in every compliance policy, set to zero (**0**) days, so devices are marked noncompliant immediately.

    When you change the default schedule, you provide a grace period in which a user can remediate issues or become compliant without being marked as noncompliant.

    This action is supported on all platforms supported by Intune.
- **Send email to end user**: This action sends an email notification to the user. When you enable this action, your options are:

    - Select a *Notification message template* that this action sends. You create a notification message template before you can assign one to this action. When you create the custom notification, you customize the message locale, subject, message body, and can include the company logo, company name, and other contact information.
    - Choose to send the message to more recipients by selecting one or more of your Microsoft Entra groups.

    Intune uses the email address in the end user's profile, not their user principal name (UPN). If no email address is on file, Intune doesn't send the notification. When the email is sent, Intune includes details about the noncompliant device in the email notification.

    This action is supported on all platforms supported by Intune.

    Note

    Notification emails are sent from microsoft-noreply@microsoft.com.

    Ensure you don't have any mailbox policies that prevent delivery of emails from these addresses. Otherwise, end users might not receive the email notification. Compliance notification emails are expected to be sent within 6 hours after a device is marked as noncompliant.
- **Remotely lock the noncompliant device**: Use this action to remotely lock a device. The user is then prompted for a PIN or password to unlock the device. For more information, see [Remote Lock](../../device-management/actions/remote-lock).

    The following platforms support this action:

    - Android device administrator
    - Android (AOSP)
    - Android Enterprise:
        - Fully Managed
        - Dedicated
        - Corporate-Owned Work Profile
        - Personally Owned Work Profile
    - iOS/iPadOS
    - macOS
- **Add device to retire list**: When this action is performed on a device, the device is added to a list of retired, noncompliant devices in the Intune admin center. You can go to **Devices** &gt; **Compliance** and select the **Retire noncompliant devices** tab to view the list. However, the device isn't retired until an administrator explicitly initiates the retirement process. When an admin retires the device from that list, retirement removes all company data from the device and removes that device from Intune management.

    The following platforms support this action:

    - Android device administrator
    - Android (AOSP)
    - Android Enterprise:
        - Fully Managed
        - Dedicated
        - Corporate-Owned Work Profile
        - Personally Owned Work Profile
    - iOS/iPadOS
    - macOS
    - Windows

    Note

    Only devices to which the **Add device to retire list** action is triggered appear in the **Retire selected devices** tab. To see a list of all devices that aren't compliant, see the **Noncompliant devices** report mentioned in [Monitor device compliance policy](monitor-policy#other-compliance-reports).

    To retire one or more devices from the list, select devices to retire and then select **Retire selected devices**. When you choose an action that retires devices, a confirmation dialog appears. It's only after confirming the intent to retire the devices that they're cleared of company data and removed from Intune management.

    Other options include *Retire all devices*, *Clear all devices retire state*, and *Clear selected devices retire state*. Clearing the retire state for a device removes the device from the list of devices that can be retired until the action to *Add device to retire list* is applied to that device again.

    Learn more about [retiring devices](../../device-management/actions/retire).
- **Send push notification to end user**: Set up this action to send a push notification about noncompliance to a device through the Company Portal app or Intune App on the device.

    The following platforms support this action:

    - Android device administrator
    - Android Enterprise:
        - Fully Managed
        - Dedicated
        - Corporate-Owned Work Profile
        - Personally Owned Work Profile
    - iOS/iPadOS

    The push notification is sent the first time a device checks in with Intune and is found to be noncompliant with the policy. When a user selects the notification, the Company Portal app or Intune app opens and displays information about why they're noncompliant. The user can then take action to resolve the issue. The message details about noncompliance are generated by Intune and can't be customized.

    Important

    Intune, the Company Portal app, and the Microsoft Intune app can't guarantee delivery of a push notification. Notifications might show up after several hours of delay, if at all. This limitation includes when users turn off push notifications.

    Don't rely on this notification method for urgent messages.

    Each instance of the action sends a notification a single time. To send the same notification again from a policy, configure more instances of the action in that policy, each with a different schedule.

    For example, you might schedule the first action for zero days and then add a second instance of the action set to three days. This delay before the second notification gives the user a few days to resolve the issue and avoid the second notification.

    To avoid sending users too many duplicate notifications, keep the following points in mind:

    - A single policy with multiple push notifications scheduled for the same day sends only one notification that day.
    - Multiple policies with the same compliance conditions and the same schedule each send a separate notification, resulting in multiple notifications to the same device on the same day.

Note

The following actions for noncompliance aren't supported for devices that are managed by a [device compliance management partner](third-party-partners):

- Send email to end user
- Remotely lock the noncompliant device
- Add device to retire list
- Send push notification to end user

## Before you begin

You can add actions for noncompliance when you configure a device compliance policy, or later by editing the policy. Add extra actions to each policy to meet your needs. Keep in mind that each compliance policy automatically includes the default action for noncompliance that marks devices as noncompliant, with a schedule set to zero days.

To use device compliance policies to block devices from corporate resources, set up Microsoft Entra Conditional Access. For guidance, see [Conditional Access in Microsoft Entra ID](/en-us/entra/identity/conditional-access/overview).

For platform-specific guidance on creating a device compliance policy, see the following articles:

- [Android](ref-android-administrator-settings)
- [Android (AOSP)](ref-android-aosp-settings)
- [Android work profiles](ref-android-enterprise-settings)
- [iOS](ref-ios-ipados-settings)
- [macOS](ref-macos-settings)
- [Windows](ref-windows-settings)

## Create a notification message template

To send email to your users, create a notification message template and associate that template to your compliance policy as an action for noncompliance. When a device is noncompliant, the details you enter in the template show in the email sent to your users.

A *notification message template* can include multiple messages that are each for a different locale. When you specify multiple messages and locales, noncompliant end users receive the appropriate localized message based on their Microsoft 365 preferred language.

Add variables to the message to create a personalized email with dynamic content. The following table describes the variables you can use in the subject line and body of the message.

| Variable name | Token to use | Description |
| --- | --- | --- |
| User name | {{UserName}} | Add the name of the primary user for the noncompliant device.  Example: `John Doe` |
| Device name | {{DeviceName}} | Add the name of the noncompliant device as it's recorded in Microsoft Intune.  Example: `John's iPad` |
| Device ID | {{DeviceId}} | Add the Intune device ID that belongs to the noncompliant device.  Example: `12ab345c-6789-def0-1234-000000000000` |
| Device OS version | {{OSAndVersion}} | Add the operating system and version of the noncompliant device.  Example: `Android 12` |

### To create the template

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Device compliance** &gt; **Notifications** &gt; **Create notification**.
3. On **Basics**, enter a friendly name for the template to help you identify it. Then select **Next**.
4. On **Header and footer settings**, add your company details and logo.

![Screenshot that shows example of the Header and footer settings page for a notification message in Intune.](media/configure-noncompliance-actions/actions-for-noncompliance-3.png)

    Your options:

    - **Email header – Show company logo** (default = *Enable*) - Upload a logo to add your organization's branding to the email templates. For more information about Company Portal branding, see [Company identity branding customization](../../app-management/configuration/configure-company-portal#customizing-the-user-experience).
    - **Email footer – Show company name** (default = *Enable*) - Enable this setting to show your company name in the email. See **Tenant Value** to review the company name on record.
    - **Email footer – Show contact information** (default = *Enable*) - Enable this setting to show your organization's contact information, such as name, phone number, and email address, in the email. See **Tenant Value** to review the contact information on record.
    - **Email footer - Show company portal website link** (default = *Disable*) - Enable this setting to include a link to the Company Portal website in the email. See **Tenant Value** to review the website link shown to users.

    Select **Next** to continue.
5. On **Notification message templates**, configure one or more messages. For each message, specify the following details:

    - **Locale**: Select the language that correlates to the device user's locale.
    - **Subject**: Add the subject line for the email. You can enter up to 78 characters.
    - **Raw HTML editor**: Turn on the HTML editor to get suggestions while adding HTML formatting and links to your message. You can use the `href` attribute to add a link (must be an HTTPS URL). Supported HTML tags include: `<a>`, `<strong>`, `<b>`, `<u>`, `<ol>`, `<ul>`, `<li>`, `<p>`, `<br>`, `<code>`, `<table>`, `<tbody>`, `<tr>`, `<td>`, `<thead>`, `<th>`. You aren't required to use the HTML editor, and can add supported HTML without turning the editor on.
    - **Message**: Create a message explaining the reason for noncompliance. You can enter up to 2,000 characters.

    To create a template with dynamic content, insert the token of a supported variable in the subject line or message. For a list of supported variables, see the table under Create a notification message template in this article.

    Important

    Be sure to only use Intune-supported HTML tags and attributes in the message body. Intune sends messages that contain other types of tags, elements, or styling as plaintext instead of HTML format. This condition includes messages that contain:

    - CSS
    - Tags and attributes not listed in this article

    Note

    Intune converts Windows-style new line characters to `<br>` HTML tags but ignores all other types of new line characters, including those for macOS and Linux. To ensure line breaks render properly in templates, we recommend using the `<br>` tag to indicate the end of a line.
6. Select the checkbox for **Is Default** for one of the messages. Intune sends your default message to users that haven't set a preferred language, or when the template doesn't include a specific message for their locale. Only one message can be set as default. To delete a message, select the ellipsis (...) and then **Delete**.

    Select **Next** to continue.
7. On **Scope tags**, select tags to limit visibility and management of this message to specific Intune admin groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next** to continue.
8. On **Review + create**, review your configurations to ensure the notification message template is ready to use. Select **Create** to complete creation of the notification.

### View and edit notifications

You can view notifications that you create in *Compliance policies* &gt; *Notifications*. From this page, select a notification to view its configuration and:

- Select **Send preview email** to send a preview of the notification email to the account you used to sign in to Intune.

    To successfully send the preview email, your account must have permissions equal to those of the following Microsoft Entra groups or Intune roles: *Intune Administrator* (also known as Intune Service Administrator) or *Policy and Profile Manager*.
- Select **Edit** for *Basics* or *Scope tags* to make a change.

Note

The preview email doesn't contain the device variables that you specify in the notification message template.

## Add actions for noncompliance

You can add optional actions when you create a compliance policy, or update an existing policy. The default mark-as-noncompliant action is added automatically and can't be removed, but you can adjust its schedule.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Compliance**.
3. Select a policy, and then select **Properties**.

    Don't have a policy yet? Create an [Android](ref-android-administrator-settings), [iOS](ref-ios-ipados-settings), [Windows](ref-windows-settings), or other platform policy.

    Note

    Devices managed by third-party device compliance partners that are targeted with device groups can't receive compliance actions at this time.
4. Select **Actions for noncompliance** &gt; **Edit**.
5. Select your **Action**:

    - **Send email to end users**: When the device is noncompliant, choose to email the user. Also:

        - Choose the **Message template** you previously created
        - Enter any **Additional recipients** by selecting groups
    - **Remotely lock the noncompliant device**: When the device is noncompliant, lock the device. This action forces the user to enter a PIN or passcode to unlock the device.
    - **Add device to retire list**: When the device is noncompliant, it's added to a retire list in the admin center. An admin must explicitly retire the device from that list before company data is removed and the device is removed from Intune management.
    - **Send push notification to end user**: Set up this action to send a push notification about noncompliance to a device through the Company Portal app or Intune App on the device.
6. Configure a **Schedule**: Enter the number of days (0 to 365) after noncompliance to trigger the action. If you enter **0**, the action takes effect immediately. After this grace period, you can enforce a [Conditional Access](../conditional-access-integration/scenarios) policy to block access to resources like email and SharePoint.

    For details about the default **Mark device noncompliant** action and how the schedule affects grace periods, see Available actions for noncompliance.

    For example, add the **Send email to end user** action with a **Schedule** of two days. If the device is still noncompliant on day two, the email is sent. To send a follow-up email on day five, add a second instance of the action with a **Schedule** of five days.

    For more information on compliance, and the built-in actions, see the [compliance overview](overview).
7. When finished, select **Add** &gt; **OK** to save your changes.