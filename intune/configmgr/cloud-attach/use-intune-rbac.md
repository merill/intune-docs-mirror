---
layout: Conceptual
title: Intune role-based access control for tenant-attached devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/use-intune-rbac
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Enable Intune role-based access control for Configuration Manager tenant-attached clients
ms.date: 2022-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 795fe6f4-e6df-9d6d-25e8-7a91b0b3b1ce
document_version_independent_id: 795fe6f4-e6df-9d6d-25e8-7a91b0b3b1ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/cloud-attach/use-intune-rbac.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/cloud-attach/use-intune-rbac
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/cloud-attach/use-intune-rbac.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f7ff83f4-42b6-6822-3887-254fe76516fc
---

# Intune role-based access control for tenant-attached devices - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in Configuration Manager version 2207, you can use Intune role-based access control (RBAC) when interacting with [tenant attached devices](../tenant-attach/client-details?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) from the Microsoft Intune admin center. For example, when using Intune as the role-based access control authority, a user with the [Help Desk Operator role](../../fundamentals/role-based-access-control/overview#built-in-roles) doesn't need an assigned security role or additional permissions from Configuration Manager. [Intune role-based access control](../../fundamentals/role-based-access-control/create-custom-role) manages the permissions to all cloud-attached device pages in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), such as [device timeline](../tenant-attach/timeline?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), [CMPivot](../tenant-attach/cmpivot-start?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), and [scripts](../tenant-attach/scripts?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json).

Important

Currently, any enforcement of Intune role-based access control for displaying and taking actions on tenant-attached devices from the Microsoft Intune admin center is optional. We recommend all admins with cloud-connected Configuration Manager environments begin verifying the role-based access control permissions from Intune.

The three high-level steps to configure Intune as the role-based access control authority for tenant-attached devices are:

- From the Configuration Manager console, disable enforcement of Configuration Manager role-based access control for cloud-attached clients
- From Intune, enable managing the user permissions for cloud-attached devices
- From Intune, verify role-based access control permissions for cloud-attached devices

## Prerequisites

- Configuration Manager version 2207 or later
- [Tenant attached devices](../tenant-attach/client-details?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json)

## Limitations

- Currently [scoping](../../fundamentals/role-based-access-control/scope-tags) isn't supported when using only Intune role-based access control for displaying and taking actions on tenant-attached devices from the Microsoft Intune admin center.
- Currently, the [**Software updates** page](../tenant-attach/software-updates) isn't available for cloud-only users when using the early update ring of Configuration Manager version 2207.

## Disable enforcement of Configuration Manager role-based access control for cloud-attached clients

To use Intune role-based access control for tenant attach rather than Configuration Manager role-based access control, use the instructions below:

1. From the Configuration Manager console, go to, **Administration** &gt; **Cloud Services** &gt; **Cloud Attach**.
2. The location of the role-based access control option varies depending on if your environment is already cloud-attached or not.

    - If your environment is already cloud-attached, open the properties for **CoMgmtSettingsProd**. If you don't have devices uploaded to the admin center, configure that option first. For more information, see [Enable cloud attach](enable).
    - If your environment isn't cloud-attached, select **Configure Cloud Attach** to open the **Cloud Attach Configuration wizard**.
3. On the **Configure upload** tab, or page in the wizard, clear the checkbox for the following option under the **Role-based Access Control** heading:

    **Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager**
4. Choose **OK** to save the change to the **CoMgmtSettingsProd** properties, or continue on to complete the [cloud attach wizard](enable).

[![Screenshot of the CoMgmtSettingsProd properties in Configuration Manager. In the screenshot, the configure upload tab is displayed with a red box outlining the role-based access control section.](media/14996522-configure-upload.png)](media/14996522-configure-upload.png#lightbox)

## Enable role-based access control from Intune

To enable Intune to manage user permissions for cloud-attached devices, use the following steps:

1. Open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in as a user that has the **Roles/Update** permission. For more information about the permission, see [custom role permissions in Intune](../../fundamentals/role-based-access-control/create-custom-role).
2. Select **Tenant administration** &gt; **Connectors and tokens** &gt; **Microsoft Endpoint Configuration Manager**.
3. In the banner, select **You can also manage user permissions from Intune. Click here to learn more about this option.**
4. The **Use Intune RBAC** flyout appears.
5. Select **On** for the **Use Intune RBAC** option, then choose **Apply**.
6. The change may take about 10 minutes to take effect.

[![Screenshot of the Microsoft Configuration Manager connectors and tokens page in Microsoft Intune admin center. The Use Intune RBAC flyout is displayed in the screenshot.](media/14996522-connectors-flyout.png)](media/14996522-connectors-flyout.png#lightbox)

## Verify role-based access control permissions from Intune

Once Intune is set to the role-based access control authority, verify the permissions for your roles. If needed, you can add these permissions to [custom roles](../../fundamentals/role-based-access-control/create-custom-role) you created in Intune.

1. Open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and sign in.
2. Select **Tenant administration** &gt; **Roles**.
3. Select a role, such as **Application Manager**, and review the permissions listed for **Cloud attached devices**. If needed, edit permissions for any [custom roles](../../fundamentals/role-based-access-control/create-custom-role) you created in Intune.

The following Intune permissions control access to the Configuration Manager cloud-attached devices:

| Permission | Description | Intune built-in roles with the permission |
| --- | --- | --- |
| Cloud attached devices\View collections | Displays the **Collections** page for Configuration Manager cloud attached devices | Application Manager, Endpoint Security Manager, Read Only Operator, School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\View resource explorer | Displays the **Resource explorer** page for Configuration Manager cloud attached devices | Application Manager, Endpoint Security Manager, Read Only Operator, School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\View timeline | Displays the **Timeline** page for Configuration Manager cloud attached devices | Application Manager, Endpoint Security Manager, Read Only Operator, School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\View software updates | Displays the **Software updates** page for Configuration Manager cloud attached devices | Application Manager, Endpoint Security Manager, Read Only Operator, School Administrator, Help Desk Operator |
| Cloud attached devices\View scripts | Displays the **Scripts** page for Configuration Manager cloud attached devices | Endpoint Security Manager, Read Only Operator, School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\Run script | Displays the **Run script** action and allows the user to run scripts on Configuration Manager cloud attached devices | School Administrator, Help Desk Operator |
| Cloud attached devices\Run CMPivot query | Displays the **CMPivot** page for Configuration Manager cloud attached devices | Endpoint Security Manager, School Administrator, Help Desk Operator |
| Cloud attached devices\View client details | Displays the **Client details** page for Configuration Manager cloud attached devices | Application Manager, Endpoint Security Manager, Read Only Operator,School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\View applications | Displays the **Applications** page for Configuration Manager cloud attached devices | Application Manager, Read Only Operator, School Administrator, Policy Profile Manager, Help Desk Operator |
| Cloud attached devices\Take application actions | Displays application actions in the **Applications** page and allows the user to take application actions on Configuration Manager cloud attached devices | Application Manager, School Administrator, Help Desk Operator |
| Remote tasks/Rotate BitLockerKeys (preview) | Initiates a key rotation for BitLocker Recovery Passwords on the device. Displays the *Recovery keys* page for Configuration Manager cloud attached devices. | Endpoint Security Manager, Help Desk Operator |

## Frequently asked questions

### I have cloud-only users that need access to tenant-attached devices in Intune, will this give them access?

Yes. When a user is cloud only, in this scenario meaning they are in Microsoft Entra ID and can access Intune, using Intune RBAC will give them access to tenant-attached devices.

### What if I have multiple Configuration Manager hierarchies connected to my tenant?

The **Use Intune RBAC** setting in the Microsoft Intune admin center applies to all of the Configuration Manager hierarchies listed in the tenant.

### What happens if the Configuration Manager and Intune settings are mismatched?

If the **Use Intune RBAC** toggle in Intune is set to **Off**, then Configuration Manager role-based access will be enforced, even if the **Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager** checkbox is cleared. Disabling the **Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager** option doesn't have any effect until the **Use Intune RBAC** toggle in Intune is set to **On**.

### What happens if my test hierarchy is configured to use Intune RBAC, but my production hierarchy isn't and they are in the same tenant?

The **Use Intune RBAC** setting applies to all of the Configuration Manager hierarchies listed in the tenant. Cloud-only users can access tenant-attached devices that are uploaded from the test hierarchy because you've also cleared the checkbox to enforce Configuration Manager RBAC. If a cloud-only user tries to access a tenant-attached device uploaded from the production environment, they'll receive an error since production devices are enforcing Configuration Manager RBAC. The cloud-only user will receive an error similar to the following message: `Unable to get device information. Make sure Azure AD and AD user discovery are configured and the user is discovered by both. Verify that the user has proper permissions in Configuration Manager.`