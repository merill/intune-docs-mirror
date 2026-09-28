---
layout: Conceptual
title: Move from Basic Mobility and Security to Intune-Migration Guide - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/migrate-from-other-mdm
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
description: Follow this migration guide to move your mobile device management from Microsoft 365 Basic Mobility and Security to Intune. Includes policy mapping and license assignment steps.
ms.date: 2026-01-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: jamiesil, dagerrit
locale: en-us
document_id: e073df24-d14f-3f93-d71c-aacb529138bf
document_version_independent_id: e073df24-d14f-3f93-d71c-aacb529138bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/migrate-from-other-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/migrate-from-other-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/migrate-from-other-mdm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 9f3af095-1f96-0c0b-eafb-4f8b70cfd008
---

# Move from Basic Mobility and Security to Intune-Migration Guide - Microsoft Intune | Microsoft Learn

**Basic Mobility and Security** is a basic set of policies included with Microsoft 365 that helps protect devices that access Microsoft 365 apps, like Outlook.

Many organizations want more advanced device management features that Microsoft Intune provides. For a comparison of the features, see [Choose between Basic Mobility and Security or Intune](/en-us/microsoft-365/admin/basic-mobility-security/choose-between-basic-mobility-and-security-and-intune).

If you use Basic Mobility and Security and want to move to Intune, this article helps you through the process. Moving to Intune requires the following major steps, which are described in more detail in this article:

1. **Prepare**:

    Review your Intune licenses, Basic Mobility and Security policies, group memberships, and devices to streamline the move.
2. **Evaluate and migrate your existing policies**:

    Use the policy mapping guidance to create new Intune policies that correspond to your existing Basic Mobility and Security policies.
3. **Assign the licenses and policies**:

    Assign the Intune licenses to users or groups, which automatically switches the users to Intune device management. When you assign licenses, users and devices are ready to receive the new Intune policies you create.
4. **Configure more settings**:

    After you move to Intune, create more policies to take advantage of the different Intune features.

This article helps you move your mobile device management (MDM) from Microsoft 365 Basic Mobility and Security to Microsoft Intune.

## Before you begin

- When you sign in to the admin centers, use an account with the following roles:

    - **License administrator** - This Microsoft Entra role lets you assign Intune licenses in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854). For more information on this role, see [Microsoft Entra built-in roles - License Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#license-administrator).
    - **Policy and profile manager** - This Microsoft Intune role lets you create and assign policies in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For more information on this role, see [Built-in roles for Microsoft Intune](role-based-access-control/ref-built-in-roles#policy-and-profile-manager).
    - **Endpoint Security Manager** - This Microsoft Intune role lets you create and assign app-based Conditional Access policies in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For more information on this role, see [Built-in roles for Microsoft Intune](role-based-access-control/ref-built-in-roles#endpoint-security-manager).
    - **Conditional Access Administrator** - This Microsoft Entra role lets you create and assign device-based Conditional Access policies in the [Microsoft Entra admin center](https://entra.microsoft.com/). For more information on this role, see [Microsoft Entra built-in roles - Conditional Access Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
- Test the steps in this article on a test users group that have devices enrolled in Basic Mobility and Security. Confirm that the policies behave as you expect.
- After you move to Intune, the existing Basic Mobility and Security policies are still available and shown in [Basic Mobility and Security](https://compliance.microsoft.com/basicmobilityandsecurity). However, the Basic Mobility and Security policies no longer apply to users that are assigned Intune licenses.

    Microsoft recommends that you remove the Basic Mobility and Security policies. You don't want these old policies to accidentally get assigned to users later. For more information, see [Turn off Basic Mobility and Security enforcement](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-turn-off).

## Step 1 - Prepare

Before you move from Basic Mobility and Security device management to Intune device management:

1. Make sure you have enough [Intune licenses](licensing) to cover all your users managed by Basic Mobility and Security. If you don't have enough licenses, group your users by priority and assign licenses in stages.
2. Review the existing Basic Mobility and Security policies and [remove any policies](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-turn-off) that you no longer need. Deleting unneeded policies reduces the number of new Intune policies you create.

    The following articles list and describe the Basic Mobility and Security policies:

    - [Set up Basic Mobility and Security](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-set-up)
    - [Configure policies in Basic Mobility and Security](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-policies-configure)

    If users are already licensed for Intune, they can get Intune policies assigned sooner than expected and their devices can lose any Basic Mobility and Security configurations.
3. Review the group memberships that are currently assigned device security policies. When you set up Basic Mobility and Security, you assigned policies to groups by using the steps at [Set up Basic Mobility and Security](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-set-up#step-4-configure-organization-settings-in-basic-mobility-and-security).

    Decide if you plan to use the same groups for your Intune policies or create new groups. If these groups include users that are already licensed for Intune, they can get Intune policies assigned sooner than expected.
4. Review the types of devices currently enrolled in Basic Mobility and Security. Unsupported [OS versions and variants](ref-supported-platforms#intune-supported-operating-systems) might continue to work, but they're not supported in Intune.
5. Be ready to create new Intune policies in the Intune admin center. These policies replace the Basic Mobility and Security policies.

## Step 2 - Evaluate existing policies and create new Intune policies

After you prepare your licenses and review the information in Step 1 - Prepare, use the policy mapping lists to create new Intune policies. The Intune policies should correspond to your existing Basic Mobility and Security policies.

1. In [Basic Mobility and Security](https://compliance.microsoft.com/basicmobilityandsecurity), review each Basic Mobility and Security policy. Use the following policy mapping references and compare them with the Intune policies. If you haven't already, decide which policies you want to create in Intune.

    - [Access requirements policy mapping](ref-policy-map-access-requirements)
    - [Configurations policy mapping](ref-policy-map-configurations)
    - [Miscellaneous policy mapping](ref-policy-map-miscellaneous)
2. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create your Intune policies based on the policy mappings. When you create the policies, you can assign them to your groups now, or assign them later.

    | Basic Mobility and Security policy | Intune policy type | Intune location |
    | --- | --- | --- |
    | [Access requirements policy mapping](ref-policy-map-access-requirements) | [Compliance policies](../device-security/compliance/overview) | [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Devices** &gt; **Compliance** |
    | [Configurations policy mapping](ref-policy-map-configurations) | [Device configuration profiles](../device-configuration/overview) | [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Devices** &gt; **Manage devices** &gt; **Configuration** |
    | [Miscellaneous policy mapping](ref-policy-map-miscellaneous) | [Device configuration profiles](../device-configuration/overview) | [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Devices** &gt; **Manage devices** &gt; **Configuration** |
    | Basic Conditional Access policies described in: -[Set up Basic Mobility and Security](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-set-up)- [Configure policies in Basic Mobility and Security](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-policies-configure) | [Conditional Access policies](../device-security/conditional-access-integration/overview) | [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) &gt; **Devices** &gt; **Conditional Access** &gt; **Classic policies** |

## Step 3 - Assign the policies in stages

Next, assign the Intune policies to the groups you choose. Keep the following points in mind:

- If you already assigned Intune policies to your groups, these policies can conflict with your new Intune policies. To learn how Intune handles conflicts, see [Common questions and answers with device policies and profiles in Microsoft Intune](../device-configuration/troubleshoot-device-profiles#compliance-and-device-configuration-policies-that-conflict).
- When the Intune policies are created, you can assign them to groups at any time. We recommend assigning the policies in stages. This staged approach helps you manage the migration process.
- After you assign your Intune policies to these groups, all Intune licensed users in the groups receive the policies, even users not previously managed by Basic Mobility and Security.

### Assign the policies

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select your policy &gt; **Assignments** &gt; **Edit**. Add your groups and **Save**. When you save, the policies are assigned.

    For the steps and guidance, see [Assign policies in Microsoft Intune](../device-configuration/assign-device-profile).

    It's important to understand how policy assignment works. When you assign Intune licenses, the Intune policies replace any existing Basic Mobility and Security policies. Users can lose settings and email configuration if they're licensed for Intune but not assigned to any Intune policies.

    Remember, the Intune license assignment is a key step in the move from Basic Mobility and Security to Intune device management.
2. For users without Intune licenses, assign Intune licenses to the users and groups you want to move to Intune. You can assign Intune licenses in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854):

    - Assign licenses to **Users**. For more information, see [Assign licenses to users](/en-us/microsoft-365/admin/manage/assign-licenses-to-users).
    - Assign licenses to **Groups**. For more information, see [Assign licenses to a group](/en-us/microsoft-365/admin/manage/manage-group-licenses).

    For more information on assigning licenses in Intune, see [Assign licenses to users so they can enroll devices in Intune](assign-licenses).

At the next [Intune device refresh cycle](../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals), the devices automatically switch to Intune management and the new policies start affecting user devices.

After you move to Intune, Microsoft recommends that you remove the Basic Mobility and Security policies. You don't want these old policies to accidentally get assigned to users later. To learn more, see [Turn off Basic Mobility and Security enforcement](/en-us/microsoft-365/admin/security-and-compliance/m365b-devices-basic-mobility-security-turn-off).

## Step 4 - Configure more settings

The Basic Mobility and Security policies are a basic set of device management settings. After you migrate to Intune, you can create more policies to take advantage of the different Intune features.

For information on a recommended minimum base set of policies, see [Get started with Intune](get-started).

To summarize, you can:

- Continue with basic set of Intune policies that protect devices and protect Microsoft 365 apps.
- Create more Intune policies to take advantage of the other features available to you.