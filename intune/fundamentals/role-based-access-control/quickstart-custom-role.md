---
layout: Conceptual
title: Create and assign a custom role in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/quickstart-custom-role
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn how to create and assign a custom Intune RBAC role with specific permissions for security operations. Follow this guide to implement least privilege access.
services: microsoft-intune
ms.topic: how-to
ms.date: 2026-01-20T00:00:00.0000000Z
locale: en-us
document_id: 36fb103f-3954-2e7a-e6ca-c70b2c817911
document_version_independent_id: 36fb103f-3954-2e7a-e6ca-c70b2c817911
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/role-based-access-control/quickstart-custom-role.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/role-based-access-control/quickstart-custom-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/role-based-access-control/quickstart-custom-role.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 22e61d4f-2268-bd35-de5a-cd03cc120eb5
---

# Create and assign a custom role in Intune - Microsoft Intune | Microsoft Learn

This article guides you through creating a custom Intune RBAC role with specific permissions for a security operations department and assigning the role to a group of operators. Custom roles help you implement least privilege access, ensuring admins can only manage the users and devices they're empowered to handle.

This article is [part of an Evaluate and Try series](../try-overview) that helps you evaluate Microsoft Intune's capabilities.

Intune includes several built-in RBAC roles that you can use. Microsoft recommends using the least-privileged role that can complete the task an administrator is expected to manage, which might be a custom role. This approach minimizes security risks and operational errors by avoiding over-privileged accounts for routine work.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Role Administrator](ref-built-in-roles#intune-role-administrator)** Microsoft Intune role
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To complete this step, you must:
> 
> - [Create a user](../tenant-administration/quickstart-create-user).
> - [Create a group](../tenant-administration/quickstart-create-group).
> 

To complete this evaluation step, you must have a group with at least one user.

## Create a custom role

When you create a custom role, you can set permissions for a wide range of actions. For the security operations role, enable *Read* permissions for a few categories so that the operator can review a device's configurations and policies.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant administrator** &gt; **Roles**. Select **Create**. From the drop-down box, select **Intune role**. The *Add Custom Role* workflow opens.

    [![Screenshot of Microsoft Intune admin center showing Tenant administration, All roles selected, and Create Intune role menu open.](media/quickstart-custom-role/add-custom-role.png)](media/quickstart-custom-role/add-custom-role.png#lightbox)
2. On the **Basics** page:

    - For **Name**, enter *Security operations*.
    - For **Description**, enter *This role lets a security operator monitor device configuration and compliance information.* Select **Next** to continue.
3. On the **Permissions** page, expand the *Corporate device identifiers* category and set *Read* to **Yes**:

    [![Screenshot of Intune Add Custom Role, Permissions page with Corporate device identifiers expanded and Read set to Yes.](media/quickstart-custom-role/corp-device-id-read.png)](media/quickstart-custom-role/corp-device-id-read.png#lightbox)

    After configuring *Read* for Corporate device identifiers, expand the following additional categories, and make the same configuration by setting *Read* to **Yes**.

    - *Device compliance policies*
    - *Device configurations*
    - *Organization*

    After the four categories are configured, select **Next** to continue.
4. On **Scope tags**, select **Next**. You don't need to configure scope tags for this evaluation scenario.
5. On **Review + Create**, select *Create*. Intune creates the custom role, which now appears on the **Intune roles | All roles** page in the Intune admin center, with a **Type** of *Custom Intune role*.

Tip

For a list of permissions by role, see [Role-based access control (RBAC) reference](ref-built-in-roles).

## Assign the role to a group

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant administration** &gt; **Roles** &gt; **All roles**.
2. On **Intune roles - All roles**, select the custom **Security operations** role you created. In the role's *Overview*, select **Assignments**, and then select **Assign**.

    [![Screenshot of Microsoft Intune Security operations Assignments page with Assign button highlighted.](media/quickstart-custom-role/assignment-workflow.png)](media/quickstart-custom-role/assignment-workflow.png#lightbox)
3. On **Basics**, enter *Sec Ops* for the name, and then select **Next**.
4. On **Admin Groups**, select **Add groups** and then choose a group that contains the users you want to assign the role's permissions to. If you created the **Contoso Testers** group in [Step 3](../tenant-administration/quickstart-create-group) of this evaluation guide, select that group.

    After adding a group, choose **Select**, and then **Next** to continue to the next page of the workflow.
5. On **Scope Groups**, select **Add groups** and then add the same group you added in the previous step. As before, choose **Select**, and then **Next** to continue to the next page of the workflow.
6. On **Scope tags**, select **Next**. You don't need to configure scope tags for this evaluation scenario.
7. On **Review + Create**, select **Create** when you're done.

    The new assignment is displayed in the list of assignments.

Now, everyone in the group is a member of the *Security operations* role and can review the following information about a device: corporate device identifiers, device compliance policies, device configurations, and organization information.

## Clean up resources

If you no longer want to use the custom role, you can delete it. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Tenant administration** &gt; **Roles** &gt; **All roles**. Locate the role, select the ellipses (...) to the left of the role description, and then select **Delete**.