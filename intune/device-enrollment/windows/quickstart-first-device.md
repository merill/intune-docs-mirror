---
layout: Conceptual
title: Enroll a Windows device - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-first-device
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: maholdaa
ms.subservice: enrollment
description: Learn how to enroll a Windows device into Microsoft Intune. Follow this step-by-step evaluation guide to test device enrollment and verify it in the Intune admin center.
services: microsoft-intune
ms.date: 2026-01-20T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e6c02608-a9ac-7e51-6099-d6243658b369
document_version_independent_id: e6c02608-a9ac-7e51-6099-d6243658b369
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/quickstart-first-device.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/quickstart-first-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/quickstart-first-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: a611b438-98eb-7cba-0e75-4f3d11092b92
---

# Enroll a Windows device - Microsoft Intune | Microsoft Learn

Enrollment ensures that all devices trying to access data within your organization are secure and compliant with your policies and requirements. Upon enrollment, the device gets access to resources like work email, files, VPN, and Wi-Fi. Employees and students who want remote access to work or school resources can also enroll their devices into Microsoft Intune.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

In this article, you:

- Try out the device user experience by enrolling a device running Windows into Microsoft Intune.
- Try out the admin user experience by verifying the enrollment in the Microsoft Intune admin center.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To complete this step, you must:
> 
> - Complete the evaluation step for [setting up automatic enrollment in Intune](quickstart-automatic-mdm).
> - Be using a [supported Windows version](../../fundamentals/ref-supported-platforms).
> 

## Enroll device

These steps guide you through using the Settings app on a Windows device to enroll the device into Intune.

1. On the device, open the Settings app, and select **Accounts**.
2. Select **Access work or school**.
3. Select **Connect** to add a work or school account.

    [![Screenshot of Windows Settings, Accounts section, showing Access work or school with Connect button highlighted.](media/quickstart-first-device/quickstart-enroll-windows-device-04.png)](media/quickstart-first-device/quickstart-enroll-windows-device-04.png#lightbox)
4. Enter the username and password for your work account. If you followed the [create a user and assign a license](../../fundamentals/tenant-administration/quickstart-create-user) evaluation step, you can use the user account that you created.
5. Wait for your device to finish registering. When you see the **You're all set!** screen, select **Done**. Your work account should now be visible under **Accounts**.

    [![Screenshot of Windows Settings showing a connected work or school account under Access work or school.](media/quickstart-first-device/quickstart-enroll-windows-device-06.png)](media/quickstart-first-device/quickstart-enroll-windows-device-06.png#lightbox)

    If you followed the previous steps, but still can't access your work or school email account and files, see [Troubleshoot Windows device access](../../user-help/troubleshooting/troubleshoot-device-access-windows).

When the device is enrolled in Intune, it starts to receive the Intune policies you create. [Common questions, answers, and scenarios with policies and profiles in Microsoft Intune](../../device-configuration/troubleshoot-device-profiles) provides more information about how policies and profiles work in Intune.

## Confirm device enrollment

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **All devices** to view the enrolled devices in Intune.
3. Verify that you have an additional device enrolled within Intune.

## Clean up resources

To unenroll the device, see [Remove your Windows device from management](../../user-help/unenrollment/unenroll-windows).