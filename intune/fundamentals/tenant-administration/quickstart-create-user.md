---
layout: Conceptual
title: Create a user in Intune and assign a license - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn how to create a user in Microsoft Intune and assign an Intune license to this user.
services: microsoft-intune
ms.topic: how-to
ms.date: 2026-01-20T00:00:00.0000000Z
ms.reviewer: jlynn
locale: en-us
document_id: a5046119-bb2b-5ac5-09a4-3c200cd569ad
document_version_independent_id: a5046119-bb2b-5ac5-09a4-3c200cd569ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/tenant-administration/quickstart-create-user.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/tenant-administration/quickstart-create-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/tenant-administration/quickstart-create-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: dc84751b-bfb2-f4ec-0fbc-957696037c57
---

# Create a user in Intune and assign a license - Microsoft Intune | Microsoft Learn

In this article, you create a user and then assign the user an Intune license. When you use Intune, each person you want to have access to company data must have their own user account. To manage access control, Intune admins can configure users at any time.

This article is [part of an Evaluate and Try series](../try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854) with the following role:
> 
> - Built-in **[User Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)** Microsoft Entra role
> 

## Create a user

A user needs a user account to enroll in Intune device management. You use this user account in other steps in this series.

To create a new user:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Users** &gt; **All users** &gt; **New user**:

    [![Screenshot that shows how to add a new user in Microsoft Intune.](media/quickstart-create-user/create-user.png)](media/quickstart-create-user/create-user.png#lightbox)
2. In the **Name** box, enter a name, such as *Dewey Kellum*:

    [![Screenshot that shows how to add user details in Microsoft Intune.](media/quickstart-create-user/create-user-02.png)](media/quickstart-create-user/create-user-02.png#lightbox)
3. In the **User name** box, enter a user identifier, such as `Dewey@contoso.onmicrosoft.com`.

    Note

    If you didn't configure your customer domain name, use the verified domain name you used to create the Intune subscription (or [free trial](../free-trial-sign-up#sign-up-for-a-free-trial)).
4. Select **Show password** and remember the automatically generated password so that you can sign in to a test device.
5. Select **Create**.

## Assign a license to a user

After you create a user, assign an Intune license to the user in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854). When you assign a license, the user can enroll their device into Intune.

To assign an Intune license to a user:

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), select **Users** &gt; **Active Users**, and then select the user you created.
2. Select the **Licenses and Apps** tab.
3. In **Select location**, select a location for the user. It might be already set.
4. In **Licenses**, select the **Intune** check box. You can select any other license that includes Intune. The [product name](/en-us/entra/identity/users/licensing-service-plan-reference) you see is also the service plan in Azure management.

    [![Select the location and Intune license in the Microsoft 365 admin center.](media/quickstart-create-user/create-user-03.png)](media/quickstart-create-user/create-user-03.png#lightbox)

    Note

    This setting uses one of your licenses for the user. If you're using a trial environment, you reassign this license to a real user in a live environment.
5. Select **Save changes**.

The new active Intune user shows that they're using an **Intune** license.

For more information, see [Add users individually or in bulk](/en-us/microsoft-365/admin/add-users/add-users).

## Assign licenses to many users or groups

The following steps allow you to assign Intune licenses to multiple users all at once:

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), select **Billing** &gt; **Licenses**. You see all licensable products that are available for your organization.
2. Select the license you want to assign.
3. Select **Users** or **Groups**, and then select **Assign licenses**.
4. Select all the users or all the groups you want to assign the license to &gt; **Assign licenses**. A notification shows the status and outcome of the process. If the assignment to the group can't be completed (for example, because of preexisting licenses in the group), you can select the notification to view details.

    The user accounts now have the permissions needed to use the service and enroll devices into management.

Tip

You can also assign Intune licenses to users by using School Data Sync (SDS). For more information, see [Overview of School Data Sync](/en-us/schooldatasync/school-data-sync-overview).

## Clean up resources

You can continue using this user in other steps of this series. When finished with this series, you can delete the user.

To delete the user:

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), select **Users** &gt; **Active users**.
2. Select the user you want to delete &gt; **Delete user** &gt; **Close**.

    ![Screenshot that shows how to delete a user in the Microsoft 365 admin center.](media/quickstart-create-user/create-user-04.png)