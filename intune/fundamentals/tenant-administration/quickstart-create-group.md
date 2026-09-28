---
layout: Conceptual
title: Create a Group to Manage Users - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group
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
description: Learn how to create a group in Microsoft Intune and add users to the groups. Use groups to manage user access to company resources and assign policies.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mattcall
locale: en-us
document_id: c3910098-f5af-a611-8d64-94f3bbb1b407
document_version_independent_id: c3910098-f5af-a611-8d64-94f3bbb1b407
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/tenant-administration/quickstart-create-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/tenant-administration/quickstart-create-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/tenant-administration/quickstart-create-group.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 42f84c37-c524-de8a-506d-4fd8b4975b27
---

# Create a Group to Manage Users - Microsoft Intune | Microsoft Learn

In this article, you use Intune to create a group based on an existing user. Use groups to manage your users and control your employees' access to your company resources. These resources can be part of your company's intranet or can be external resources, such as SharePoint sites, SaaS apps, or web apps.

This article is [part of an Evaluate and Try series](../try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[User Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)** Microsoft Entra role
> 

## All users and All devices groups

When you create an Intune subscription, Intune automatically creates the **All Users** and **All Devices** groups. These groups have built-in optimizations. Use these groups when you want to apply policies to all users or all devices in your organization.

When you create your policies, assign your policies to these built-in groups or the groups you create.

For more information about using groups in Intune, like using filters, and assigning to user groups vs. device groups, see:

- [Assign policies in Microsoft Intune](../../device-configuration/assign-device-profile)
- [Assign Apps to Groups With Microsoft Intune](../../app-management/deployment/assign-groups)

## Create a group

In this step, you create a group. You use this group later in another task in this evaluation series.

To create a group:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** &gt; **New group**.
2. In the **Group type** dropdown box, select **Security**.
3. In the **Group name** field, enter the name for the new group (for example, **Contoso Testers**).
4. Add a **Group description** for the group.
5. Set the **Membership type** to **Assigned**.
6. Under **Members**, select the link and add one or more members for the group from the list. If you created a user in [Step 2 - Create a user in Intune and assign the user a license](quickstart-create-user), you can add that user to this group.

    [![Screenshot of creating a group in Microsoft Intune.](media/quickstart-create-group/quickstart-use-groups-01.png)](media/quickstart-create-group/quickstart-use-groups-01.png#lightbox)
7. Choose **Select** &gt; **Create**.

After you create the group, it appears in the list of **All groups**.

Note

By using the added support for soft-deleting groups by Microsoft Entra, Intune displays those groups as soft deleted in the admin center when they're in that state. When you soft-delete groups, the process removes their assignments. When you restore these groups, the process also restores any policy assignments.