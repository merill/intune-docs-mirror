---
layout: Conceptual
title: Set up enrollment notifications in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/setup-notifications
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
description: Set up enrollment notifications in Intune for employees or students.
ms.date: 2024-06-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: maholdaa
locale: en-us
document_id: 39937035-2217-ddae-38b7-a2da85cb2f78
document_version_independent_id: 39937035-2217-ddae-38b7-a2da85cb2f78
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/setup-notifications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/setup-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/setup-notifications.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/858ed2c1-cb51-4a4a-848b-5313e2dd9540
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c5b5e0b8-79cd-42fb-b5f0-87c237daf614
platformId: ac40408b-303e-2e42-a8f9-990da0c03a07
---

# Set up enrollment notifications in Intune - Microsoft Intune | Microsoft Learn

Set up enrollment notifications in Microsoft Intune to notify employees of newly enrolled devices. Enrollment notifications are sent to assigned users via your selected method: email or push notification. Within a notification, you can:

- Add a custom message for the user, with information about how to report an unrecognized device.
- Apply your tenant's branding and customization settings (email notifications only).

Enrollment notifications are supported on these devices:

- Android devices in bring-your-own-device (BYOD) scenarios.
- iOS/iPadOS devices in BYOD scenarios such as device enrollment. However, enrollment notifications aren't supported with user enrollment.
- macOS devices in BYOD scenarios such as device enrollment.
- Devices running Windows, excluding Microsoft Entra hybrid joined devices.
- Windows Autopilot devices, excluding userless scenarios such as Windows Autopilot for pre-provisioned deployment.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Example

The following example image shows what an enrollment notification looks like to a device user.

![Example image of an enrollment notification configured in Intune, notifying the recipient that a device named *Nia's iPhone&quot; was enrolled, and includes HTML elements such as bolded font and a hyperlink, device details, contact information, and privacy statement.](media/setup-notifications/enrollment-notification-message.png)

## Requirements

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To create enrollment notifications, sign in as [**Intune Administrator**](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

![](../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> [Configure Microsoft Intune branding and customization settings](../app-management/configuration/configure-company-portal) under **Tenant administration** &gt; **Customization**.

![](../media/icons/16/enrollment.svg)**Enrollment methods**

> 
> Enrollment notifications work with user-driven enrollment methods. They aren't supported in userless enrollment scenarios, or when provisioning Windows 365 Cloud PCs.

## You should know

Email notifications appear in the user's inbox. Push notifications appear in the Intune Company Portal apps for iOS/iPadOS, macOS, and Android. Enrollment push notifications aren't supported in the Company Portal for Windows, so they'll never appear there.

## Create an enrollment notification

Tip

Use the built-in HTML editor to format and style email notifications. Intune supports the following HTML tags: `<a>`, `<strong>`, `<b>`, `<u>`, `<ol>`, `<ul>`, `<li>`, `<p>`, `<br>`, `<code>`, `<table>`, `<tbody>`, `<tr>`, `<td>`, `<thead>`, and`<th>`. It also supports the `href` attribute for hyperlinks, but only for HTTPS links.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as an [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Windows**, **Apple**, or **Android** tab.
4. Choose **Enrollment notifications**.
5. Apple and Android notifications are supported on iOS, macOS, Android Enterprise, and Android device administrator, respectively. Select the tab that corresponds to the OS you're managing.

    Your options for Apple enrollment are:

    - **iOS/iPadOS Notifications**
    - **macOS Notifications**

    Your options for Android enrollment are:

    - **Android Enterprise Notifications**
    - **Android device administrator Notifications**
6. Select **Create notifications**.
7. In **Basics**, configure the following settings:

    - **Name**: Enter a descriptive name for the notification. Name your notifications so you can easily identify them later.
    - **Description**: Enter a description for the notification. This setting is optional, but recommended.
8. Select **Next**.
9. In **Notification settings**, configure the notification messages.

    The options for push notifications are:

    - **Send Push Notification**: Flip the switch **On** to enable and create a push notification.
    - **Subject**: Enter the subject of the enrollment notification.
    - **Message**: Enter your message, explaining the purpose of the notification. The character limit is 2000.

    The options for email notifications are:

    - **Send Email Notification**: Flip the switch **On** to enable and create an email notification.
    - **Subject**: Enter the subject of the enrollment notification.
    - **Message**: Enter your message. The character limit is 2000.
    - **Raw HTML editor**: Flip the switch **On** to enable HTML formatting.

    The options for branding and customization are:

    - **Show company logo**: Flip the switch **On** to make your organization's logo visible in the email header. This option becomes available after you've configured Company Portal branding in your tenant.
    - **Show device details**: Device details are turned off by default. Flip the switch **On**to show device details in the footer of the email. Emails with device details can take longer to deliver. Intune may not be able to populate all details. Details include:
        - Device name
        - Model
        - OS
        - OS version
        - Serial number

    Note

    Device name does not always reflect the most recent device name in a tenant. Some devices have a pre-configured device name from Intune that changes once enrolled and given timing, this pre-configured name can sometimes show in the Device details of the message. The Company portal website link will always show the most recent and accurate device name.

- **Show company name**: Flip the switch **On**to make your organization's name visible in the footer of the email. The tenant value is automatically populated.
    - **Show contact information**: Flip the switch **On** to show your organization's contact information. The tenant value is automatically populated.
    - **Show Company portal website link**: Flip the switch **On** to show a link to the Company Portal website. The tenant value is automatically populated.

1. Select **Next**.
2. Optionally, assign a scope tag, like `US-NC IT Team` or `JohnGlenn_ITDepartment`, to limit management of the notification to specific IT groups. Then select **Next**.
3. In **Assignments**, select the users or groups receiving the notification. 
    Note

    The *exclude* feature isn't available for enrollment notifications.
4. Select **Next**.
5. In **Review + create**, review the notification details, and then select **Create**.

Enrollment notifications are sent out to assigned groups when enrollment is triggered. Return to **Enrollment notifications** to view and edit notifications, or change priority level.