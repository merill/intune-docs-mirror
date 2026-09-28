---
layout: Conceptual
title: Add and Assign an App - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/quickstart-add-assign
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Add
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how to add and assign apps to user groups in Microsoft Intune. Ensure your workforce has access to the apps they need.
ms.date: 2026-01-20T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: d0e5e51e-6cc5-7455-b57f-34a059ad493a
document_version_independent_id: d0e5e51e-6cc5-7455-b57f-34a059ad493a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/quickstart-add-assign.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/quickstart-add-assign
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/quickstart-add-assign.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1fca3389-37ea-8fa7-bc1a-75a584cbb6f3
---

# Add and Assign an App - Microsoft Intune | Microsoft Learn

In this article, you use Intune to add and assign an app to your company's workforce. The goal is to assign apps that users need to do their work. For example, you can assign Microsoft 365 Apps so users can read email, and create and edit documents and spreadsheets.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Application Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#application-manager)** Microsoft Intune role
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To complete this step, you must:
> 
> - [Create a user](../../fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](../../fundamentals/tenant-administration/quickstart-create-group).
> - [Enroll a device](../../device-enrollment/windows/quickstart-automatic-mdm)
> 

## Add the app to Intune

When you add an app to Intune, you assign that app to the users and groups that need it. You can choose to assign the app to any group you choose, including the group you created in [Step 3 - Create a group](../../fundamentals/tenant-administration/quickstart-create-group).

Use the following steps to add an app to Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Apps** &gt; **All Apps** &gt; **Create**.
2. In the **App type** drop-down box, select **Windows 10 and later** from **Microsoft 365 Apps**.
3. Click **Select**. The **Add app** steps are displayed.
4. Confirm the default details in the **App suite information** step and select **Next**.
5. Confirm the default settings in the **App settings** step and select **Next**.
6. Select the group assignments for the app. You can select the group you created in [Step 3 - Create a group](../../fundamentals/tenant-administration/quickstart-create-group). For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).
7. Select **Next** to display the **Review + create** page. Review the values and settings you entered for the app.
8. When you're done, select **Create** to add the app to Intune.

## Update the app assignment (optional)

After you add an app to Microsoft Intune, you can assign the app to more groups of users or devices at any time.

Use the following steps to update an app assignment:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Apps** &gt; **All Apps**.
2. Select the app that you want to assign to a group.
3. Select **Properties**. Next to **Assignments**, select **Edit**.
4. Select **Add Group** under the **Required** section. The **Select group** pane is displayed.
5. Find the group that you want to add and choose **Select** at the bottom of the pane.
6. Select **Review + save** &gt; **Save** to assign the group.

You now have assigned the app to another group.

## Install the app on the enrolled device

End users must install and use the Company Portal app to install an app made available by Intune. You, acting as an end user, can use the following steps to verify that the app is available to the user on Intune-enrolled devices.

1. Sign in to your enrolled Windows device. You can use the device you enrolled in [Step 5 - Enroll a Windows device in Microsoft Intune](../../device-enrollment/windows/quickstart-first-device).

    Important

    - The device must be enrolled in Intune.
    - You must sign in to the device with an account that belongs to the same group you assigned the app to.
2. From the **Start** menu, open the **Microsoft Store**. Then, find the **Company Portal** app and install it.
3. Launch the **Company Portal** app.
4. Select the app that you added to Intune. In this article, you added the **Microsoft 365 Apps** suite.

    Note

    If you don't successfully assign any apps to the Intune user, you see the following message: `Your IT administrator did not make any apps available to you.`
5. Select **Install**.

If your business needs require that you assign the Company Portal app to your workforce, you can manually assign the Windows Company Portal app directly from Intune. For more information, see [Manually add the Windows Company Portal app by using Microsoft Intune](../configuration/configure-company-portal).