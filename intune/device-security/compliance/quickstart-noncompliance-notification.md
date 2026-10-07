---
layout: Conceptual
title: Send Email Notifications to Noncompliant Devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/quickstart-noncompliance-notification
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-device-compliance
ms.subservice: protect
description: Learn how to create notification templates and send email alerts to users with noncompliant devices in Microsoft Intune. Configure actions for noncompliance.
ms.date: 2026-01-20T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: tycast
locale: en-us
document_id: 4ac95a2e-20d4-a933-947f-3b087d5fd467
document_version_independent_id: 4ac95a2e-20d4-a933-947f-3b087d5fd467
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/quickstart-noncompliance-notification.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/quickstart-noncompliance-notification
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/quickstart-noncompliance-notification.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: fc85be3f-98e5-8853-b75d-3f1653e0c4e6
---

# Send Email Notifications to Noncompliant Devices - Microsoft Intune | Microsoft Learn

Learn how to send email notifications to noncompliant devices using Microsoft Intune. This article walks you through creating notification templates and configuring actions that alert users when their devices fail to meet compliance requirements.

In this article, you use Microsoft Intune to send an email notification to the members of your workforce that have noncompliant devices.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

When Intune detects a device that isn't compliant, Intune immediately marks the device as noncompliant. When a device isn't compliant, Intune allows you to add actions for noncompliance, which gives you flexibility to decide what to do. For example, you can give users a grace period to be compliant before blocking noncompliant devices using [Microsoft Entra Conditional Access](../conditional-access-integration/overview).

When a device isn't compliant, a common action is to email the device user. You can customize the email notification. Specifically, you can customize the recipients, subject, and message body, including company logo, and contact information. Intune also includes details about the noncompliant device in the email notification.

Note

Admins need to set the target language for the notification template in the Intune admin center. When the message is sent, its language is determined by the user's preferred language in Microsoft Entra ID.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Policy and Profile manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** Microsoft Intune role
> 

## Create a notification message template

To send email to your users, create a notification message template. When a device is noncompliant, the details you enter in the template are shown in the email sent to your users.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** &gt; **Compliance**.
2. Select the **Notifications** tab and then select **Create notification**.
3. Enter the following information for the **Basics** step:

    - **Name**: *Contoso Admin*
    - **Email header – Include company logo**: Set to **Enabled** to show your organization's logo.
    - **Email footer – Include company name**: Set to **Enabled** to show your organization's name.
    - **Email footer – Include contact information**: Set to **Enabled** to show your organization's contact information.
    - **Company Portal Website Link**: Set to **Disabled**.
4. Select **Next**.
5. Enter the following information for the **Notification message templates** step:

    - **Subject**: *Device compliance*
    - **Message**: *Your device is currently not meeting our organization's compliance requirements.*
6. Select **Next** and review your notification.
7. Select **Create**. The notification message template is ready to use.

    Note

    You can also edit a Notification template that you previously created.

For details about setting your company name, company contact information, and company logo, see the following articles:

- [Company information and privacy statement](../../app-management/configuration/configure-company-portal#configuration)
- [Support information](../../app-management/configuration/configure-company-portal#support-information)
- [Customizing the user experience](../../app-management/configuration/configure-company-portal#customizing-the-user-experience).

## Add a noncompliance policy

When you create a device compliance policy, Intune automatically creates an action for noncompliance. Intune marks devices as noncompliant when they fail to meet your compliance policy. You can customize how long the device is marked as noncompliant. You can also add another action when you create a compliance policy, or update an existing compliance policy.

The following steps create a compliance policy for Windows devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Compliance**.
2. On the **Policies** tab, choose **Create policy**.
3. Under **Platform**, select **Windows 10 and later**.
4. Select **Create**.
5. Enter the following information in the **Basics** step followed by **Next**:

    - **Name**: *Windows compliance*
    - **Description**: *Windows compliance policy*
6. Select **System Security** to display the device security-related settings.
7. Configure the following options:

    - Set **Require a password to unlock mobile devices** to **Require**. This setting specifies whether to require users to enter a password before access is granted to information on their mobile devices.
    - Set **Minimum password length** to **6**. This setting specifies the minimum number of digits or characters in the password.
8. Select **Next** for each of the remaining steps until you reach the **Review + create** step. Select **Create** to create your compliance policy.

## Add an action for noncompliance

After you create a noncompliance policy, set an action for when a device is out of compliance.

The following steps show how to create an action for noncompliance for Windows devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance**.
2. Select your Windows compliance policy from the list.
3. Select **Properties**.
4. Next to the **Action for noncompliance** section, choose **Edit**.
5. In the **Action** drop-down box, select **Send email to end users**.
6. In the **Schedule (days after noncompliance)** drop-down box, select **0**.
7. Under **Message template**, select **None selected** to display the **Notification message templates** pane.
8. Select the template you created earlier in this topic, and then choose **Select** to select the message template.
9. Select **Review + save** &gt; **Save** to save your compliance policy.

## Assign the policy

You can assign the compliance policy to a specific group of users or to all users. When Intune recognizes that a device is noncompliant, it notifies the user that they must update their device to meet the compliance policy. Use the following steps to assign the policy.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Compliance** and select the **Windows compliance** policy that you created earlier.
2. Select **Properties**.
3. Next to **Assignments**, select **Edit**.
4. In the **Assign to** drop-down box, select **All Users**. Any user that has a **Windows 10 and later** device that doesn't meet this compliance policy is notified.

    Note

    You can include and exclude groups when assigning compliance policies.
5. Select **Review + save** &gt; **Save**.

When you successfully create and save the policy, it appears in the list of **Compliance policies - Policies**. Notice in the list that **Assigned** is set to **Yes**.