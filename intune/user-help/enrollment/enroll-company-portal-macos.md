---
layout: Conceptual
title: Enroll your Mac with Intune Company Portal - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-company-portal-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Enroll your personal Mac for work using the Company Portal app.
ms.date: 2025-07-29T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: 6e3dcfc9-6a6f-0b05-b6ff-94c14d578fe6
document_version_independent_id: 6e3dcfc9-6a6f-0b05-b6ff-94c14d578fe6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-company-portal-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-company-portal-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-company-portal-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7234a8c6-cccf-8b04-2508-1aa31977c3d3
---

# Enroll your Mac with Intune Company Portal - Microsoft Intune | Microsoft Learn

Set up secure, remote access to work emails, files, and apps on your personal Mac. This article describes how to install the Company Portal app, enroll your Mac for work, and get troubleshooting help.

## What to expect from the Company Portal app

During initial setup, the Company Portal app requires you to sign in and authenticate with your work account. Company Portal then informs you of any device settings you need to change to meet your organization's requirements. For example, your organization could require you to make your device PIN longer or require you to update your operating system. After you enroll your device, Company Portal helps you maintain the secure work access. The app notifies you of new policies and requirements and gives you the chance to adjust your settings so that you can continue to work uninterrupted.

For more information about the Company Portal app for macOS, see [What happens when I install the Company Portal app and enroll my device?](effects-macos)

## Before you begin

Your device must be running macOS 11 or later.

Note

During installation and enrollment, you might be prompted to allow Company Portal to use confidential information that's stored in your keychain. These prompts are part of Apple security. When you get the prompt, type in your login keychain password and select **Always Allow**. If you press **Enter** or **Return** on your keyboard, the prompt will select **Allow**, which means you may continue to receive prompts.

## Install Company Portal app

1. Go to [Enroll My Mac](https://go.microsoft.com/fwlink/?linkid=853070).
2. Wait while the Company Portal installer .pkg file downloads. Open the installer when it's ready.
3. On the **Introduction** page, select **Continue**.
4. On the **License** page, read through the Microsoft Application License Terms. Select **Continue**.
5. Select **Agree** to agree to the terms of the software license agreement.
6. On the **Installation Type** page, select **Install**.
7. Enter your device password or registered fingerprint. Then select **Install Software**.
8. Wait for Company Portal to finish installing.
9. Open Company Portal from the Applications folder.

Important

Microsoft AutoUpdate might open after enrollment and update your Microsoft software. After all updates are installed, open the Company Portal app. For the best setup experience, install the latest versions of Microsoft AutoUpdate and Company Portal.

## Enroll your Mac

1. Sign in to the Company Portal app with your work or school account.
2. On the **Set up access** page, select **Begin**.
3. Review the privacy information. Then select **Continue**.
4. On the **Install management profile** page, select **Download profile**.
5. Your macOS system settings open in a new window. The management profile you downloaded is shown.

    1. Select the profile to open it.
    2. Review the details of the enrollment profile. Select **Install...**
    3. When asked to confirm installation, select **Install**.
    4. Enter your device password to allow the profile to enroll your device. Then select **Enroll**.
6. Wait while the management profile installs and then enrolls your device.
7. Return to the Company Portal app and verify that there's a green checkmark next to **Install management profile**.
8. Your organization may require changes to the device settings. In Company Portal, select the device. Under **Status**, review the list of required changes. Select **Learn more** to read more about the requirements.

    Tip

    Select **How to resolve this**, where applicable, to view related help documentation in a web browser.
9. After you make all changes, select **Retry**. Wait while Company Portal rechecks your device settings and refreshes the status.
10. When setup is complete, select **Done**.

Your device is ready to use for work or school. Sign in to the Company Portal app or website anytime to view and manage it.

## Enrollment profile details

You can view and finish installing the enrollment profile on your device in the Apple system settings app. Before you install the enrollment profile, make sure it contains the following information:

- **Verification status**: **Verified**
- **Description**: **Install this profile to get access to your company apps**.
- **Signed**: **IOSProfileSigning.manage.microsoft.com**
- **Received**: States the day, month, year, and time that the enrollment profile was received on the device.
- **Settings**: **Profile Service Enrollment**
- **Profile service enrollment description**: **Encrypted Profile Service**

## Troubleshooting and feedback

Contact your IT support person to troubleshoot problems with enrollment or the Company Portal app. If necessary, you can share your app logs with your support person via the Company Portal app.

1. In the Company Portal app, open the **Help** menu.
2. Select **Send diagnostic report**. Wait while Company Portal app logs are sent to Microsoft support and Intune Company Portal developers. This information is used to assist with troubleshooting should your support person need more help.
3. Copy your incident ID for future reference.
4. Select **Email Logs** to report the problem to your support person. Type in what you experienced in the body of the email. To find your support person's email address, go to the Company Portal app and select **Support**.

To share your feedback and suggestions with Intune Company Portal app developers, go to **Help** &gt; **Send Feedback**.

## Updating the Company Portal app

Updating the Company Portal app is done the same way as any other Office app, through Microsoft AutoUpdate for macOS. For more information, see [Update Office for Mac automatically](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).