---
layout: Conceptual
title: Walkthrough-Create a settings catalog policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/tutorial-group-policy-migration
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- intune-scenario
ms.subservice: configuration
description: This tutorial or walkthrough steps through creating and comparing an on-premises Administrative Templates (ADMX) Group Policy and Microsoft Intune cloud-based settings catalog policy. It shows similar settings in on-premises and the Intune settings catalog to create and manage policies for Office, Windows, and Microsoft Edge on Windows 10/11 client devices.
ms.date: 2026-06-10T00:00:00.0000000Z
ms.topic: tutorial
ms.reviewer: mayurjadhav
locale: en-us
document_id: 460d58f3-a5b6-4599-ffa2-f4a726ca9626
document_version_independent_id: 460d58f3-a5b6-4599-ffa2-f4a726ca9626
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/tutorial-group-policy-migration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/tutorial-group-policy-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/tutorial-group-policy-migration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 7b437b14-a53a-a881-7b45-046f1af089d1
---

# Walkthrough-Create a settings catalog policy - Microsoft Intune | Microsoft Learn

Note

This walkthrough was created as a technical workshop and updated to apply to the Intune settings catalog. It has more prerequisites than typical walkthroughs, as it compares using and configuring settings catalog policies in Intune and on-premises Group Policy Administrative Templates (ADMX).

Group policy and ADMX templates include settings you can configure on Windows devices. These settings are used and managed by Mobile Device Management (MDM) providers, like Microsoft Intune, to configure features and settings on Windows devices. For example, you can turn on Design Ideas in PowerPoint, set a home page in Microsoft Edge, and more.

These settings are built into the Microsoft Intune [settings catalog](./). In a settings catalog profile, you configure the settings you want to include, and then assign this profile to your devices.

In this walkthrough, you:

- Get introduced to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Create user groups and create device groups.
- Compare the settings in Intune with on-premises ADMX settings.
- Create different settings catalog policies, and configure the settings that target the different groups.

By the end of this lab, you can use Intune to manage your users, and deploy settings catalog policies.

This feature applies to:

- Windows
- Microsoft Edge version 77 and newer

Tip

- For an overview of the Intune settings catalog, go to [Use the settings catalog to configure settings](./).
- For more information on ADMX policies, go to [Understanding ADMX-backed policies](/en-us/windows/client-management/mdm/understanding-admx-backed-policies).

## Prerequisites

- A Microsoft 365 E3 or E5 subscription, which includes Intune and Microsoft Entra ID P1 or P2. If you don't have an E3 or E5 subscription, [try it for free](/en-us/microsoft-365/commerce/try-or-buy-microsoft-365).

    For more information on what you get with the different Microsoft 365 licenses, go to [Transform your Enterprise with Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise/microsoft365-plans-and-pricing).
- Microsoft Intune is configured as the **Intune MDM Authority**. For more information, go to [Set the mobile device management authority](../../fundamentals/setup-mdm-authority).

    ![Screenshot that shows how to set the MDM authority to Microsoft Intune in your tenant status.](media/tutorial-group-policy-migration/tenant-status.png)
- On an on-premises Active Directory domain controller (DC):

    1. Copy the following Office and Microsoft Edge templates to the [Central Store (sysvol folder)](/en-us/troubleshoot/windows-client/group-policy/create-and-manage-central-store):

        - [Office administrative templates](https://www.microsoft.com/download/details.aspx?id=49030)
        - [Microsoft Edge policy file](https://www.microsoft.com/edge/business/download)
    2. Create a group policy to push these templates to a Windows Enterprise administrator computer in the same domain as the DC. In this walkthrough:

        - The group policy we created with these templates is named **OfficeandEdge**. You'll see this name in the images.
        - The Windows Enterprise administrator computer we use is named the **Admin computer**.

        In most organizations, a domain administrator has two accounts:

        - A typical domain work account
        - A different domain administrator account used only for domain administrator tasks, like group policy

        The purpose of this **Admin computer** is for administrators to sign in with their domain administrator account, and access tools designed for managing group policy.
- On this **Admin computer**:

    - Sign in with a Domain Administrator account.
    - Add the **RSAT: Group Policy Management Tools**:

        1. Open the **Settings** app &gt; **System** &gt; **Add an optional feature** &gt; **View features**.
        2. Select **RSAT: Group Policy Management Tools** &gt; **Add**.

            Wait while Windows adds the feature. When complete, it eventually shows in the **Windows Administrative Tools** app.

            [![Screenshot that shows the Windows Administrative Tools apps, including the Group Policy Management app.](media/tutorial-group-policy-migration/windows-administrative-tools-app.png)](media/tutorial-group-policy-migration/windows-administrative-tools-app.png#lightbox)
    - Be sure you have internet access and administrator rights to the Microsoft 365 subscription, which includes the Intune admin center.

## Open the Intune admin center

1. Open a Chromium-based web browser, like Microsoft Edge.
2. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Sign in with the following account:

    **User**: Enter the administrator account of your Microsoft 365 tenant subscription. **Password**: Enter its password.

The Intune admin center is focused on device management, and includes Azure services, like Microsoft Entra ID. You might not see the **Microsoft Entra ID** and **Azure** branding, but you're using them.

You can also open the Intune admin center from the [Microsoft 365 admin center](https://admin.microsoft.com):

1. Go to https://admin.microsoft.com.
2. Sign in with the administrator account of your Microsoft 365 tenant subscription.
3. Select **Show all** &gt; **Admin centers** &gt; **Microsoft Intune**. The Intune admin center opens.

    ![Screenshot that shows the admin centers in the Microsoft 365 admin center.](media/tutorial-group-policy-migration/microsoft-365-admin-centers.png)

## Create groups, and add users

On-premises policies are applied in the LSDOU order - local, site, domain, and organizational unit (OU). In this hierarchy, OU policies overwrite local policies, domain policies overwrite site policies, and so on.

In Intune, policies are applied to users and groups you create. There isn't a hierarchy. For example:

- If two policies update the same setting, then the setting shows as a conflict.
- If two compliance policies are in conflict, then the most restrictive policy applies.
- If two configuration profiles are in conflict, then the setting isn't applied.

For more information, go to [Common questions, issues, and resolutions with device policies and profiles](../troubleshoot-device-profiles#compliance-and-device-configuration-policies-that-conflict).

In these next steps, you create security groups, and add users to these groups. You can add a user to multiple groups. For example, it's normal for a user to have multiple devices, like a Surface Pro for work, and an Android mobile device for personal. And, it's normal for a person to access organizational resources from these multiple devices.

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** &gt; **New group**.
2. Enter the following settings:

    - **Group type**: Select **Security**.
    - **Group name**: Enter **All Windows student devices**.
    - **Membership type**: Select **Assigned**.
3. Select **Members**, and add some devices.

    Adding devices is optional. The goal is to practice creating groups, and knowing how to add devices. If you're using this walkthrough in a production environment, then be aware of what you're doing.
4. **Select** &gt; **Create** to save your changes.

    Don't see your group? Select **Refresh**.
5. Select **New group**, and enter the following settings:

    - **Group type**: Select **Security**.
    - **Group name**: Enter **All Windows devices**.
    - **Membership type**: Select **Dynamic Device**.
    - **Dynamic device members**: Select **Add dynamic query**, and configure your query:

        - **Property**: Select **deviceOSType**.
        - **Operator**: Select **Equals**.
        - **Value**: Enter **Windows**.

        1. Select **Add expression**. Your expression is shown in the **Rule syntax**:

            [![Screenshot that shows how to create a dynamic group query, and add expressions in Microsoft Intune.](media/tutorial-group-policy-migration/dynamic-group-query.png)](media/tutorial-group-policy-migration/dynamic-group-query.png#lightbox)

            When users or devices meet the criteria you enter, they're automatically added to the dynamic groups. In this example, devices are automatically added to this group when the operating system is Windows. If you're using this walkthrough in a production environment, then be careful. The goal is to practice creating dynamic groups.
        2. **Save** &gt; **Create** to save your changes.
6. Create the **All Teachers** group with the following settings:

    - **Group type**: Select **Security**.
    - **Group name**: Enter **All Teachers**.
    - **Membership type**: Select **Dynamic User**.
    - **Dynamic user members**: Select **Add dynamic query**, and configure your query:

        - **Property**: Select **department**.
        - **Operator**: Select **Equals**.
        - **Value**: Enter **Teachers**.

            1. Select **Add expression**. Your expression is shown in the **Rule syntax**.

                When users or devices meet the criteria you enter, they're automatically added to the dynamic groups. In this example, users are automatically added to this group when their department is Teachers. You can enter the department and other properties when users are added to your organization. If you're using this walkthrough in a production environment, then be careful. The goal is to practice creating dynamic groups.
            2. **Save** &gt; **Create** to save your changes.

### Talking points

- Dynamic groups are a feature in some Microsoft Entra ID licenses. If you don't have the correct Microsoft Entra ID license, then you're only licensed to create assigned groups. For more information on dynamic groups, go to:

    - [Understand and manage dynamic group processing in Microsoft Entra ID](/en-us/entra/identity/users/manage-dynamic-group)
    - [Manage rules for dynamic membership groups in Microsoft Entra ID](/en-us/entra/identity/users/groups-dynamic-membership)
    - [Create simpler and faster rules for dynamic membership groups](/en-us/entra/identity/users/groups-dynamic-rule-more-efficient)
    - [Optimize rule efficiency](/en-us/entra/identity/users/manage-dynamic-group#optimize-rule-efficiency)
- For Intune-only device targeting based on properties like OS type or manufacturer, consider using [assignment filters](../../fundamentals/filters/overview) instead of dynamic device groups. Filters evaluate at check-in without depending on group membership processing, and can simplify your targeting architecture. Dynamic groups remain necessary for cross-workload scenarios (Conditional Access, licensing) and user-based grouping. For more information, go to [Performance recommendations for grouping, targeting, and filtering in large Microsoft Intune environments](../../fundamentals/filters/performance-recommendations).
- Your Microsoft Entra ID license can include other services that are commonly used when managing apps and devices, including [multifactor authentication (MFA)](/en-us/entra/identity/authentication/concept-mfa-howitworks) and [Conditional Access](/en-us/entra/identity/conditional-access/overview).
- Many administrators ask when to use user groups and when to use device groups. For some guidance, go to [User groups vs. device groups](../assign-device-profile#user-groups-vs-device-groups).
- Remember, a user can belong to multiple groups. Consider some of the other dynamic user and device groups you can create, like:

    - All Students
    - All Android devices
    - All iOS/iPadOS devices
    - Marketing
    - Human Resources
    - All Charlotte employees
    - All Redmond employees
    - West coast IT administrators
    - East coast IT administrators

The users and groups created are also seen in the [Microsoft 365 admin center](https://admin.microsoft.com) and [Microsoft Entra admin center](https://entra.microsoft.com). You can create and manage groups in all these areas for your tenant subscription. **If your goal is device management, then use the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431)**.

### Review group membership

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Users** &gt; **All users** &gt; select the name of any existing user.
2. Review some of the information you can add or change. For example, look at the **Properties** you can configure, like Job Title, Department, City, Office location, and more. You can use these properties in your dynamic queries when you create dynamic groups.
3. Select **Groups** to see the membership of this user. You can also remove the user from a group.
4. Select some of the other options to see more information, and what you can do. For example, look at the assigned license, the user's devices, and more.

### What did I just do?

In the Intune admin center, you created new security groups, and added existing users and devices to these groups. We use these groups in later steps in this tutorial.

## Create a settings catalog policy in Intune

In this section, we create a settings catalog policy in Intune, look at some settings in on-premises **Group Policy Management**, and compare the same setting in Intune. The goal is to show a setting in group policy, and show the same setting in Intune.

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
2. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Create**.
4. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, enter **Windows student devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
5. Select **Next**.
6. In **Configuration settings**, select **Add settings**. You see a list of all the settings.

    [![Screenshot that shows the settings catalog settings picker in Microsoft Intune.](media/tutorial-group-policy-migration/settings-catalog-settings-picker.png)](media/tutorial-group-policy-migration/settings-catalog-settings-picker.png#lightbox)

    You can also filter settings that apply to **devices** and settings that apply to **users**, and **Search** for settings:

    ![Screenshot that shows how you can filter and search in the settings catalog settings picker in Microsoft Intune.](media/tutorial-group-policy-migration/settings-catalog-filter-search.png)
7. In search, enter **download**. All the policy settings with "download" in their name are filtered and shown in the list:

    [![Screenshot that shows how to search for policies with a keyword in the settings catalog in a Microsoft Intune.](media/tutorial-group-policy-migration/settings-catalog-download-settings.png)](media/tutorial-group-policy-migration/settings-catalog-download-settings.png#lightbox)
8. Go to the **Microsoft Edge** category &gt; select **SmartScreen settings**. Notice the SmartScreen policy settings with "download" in their name are filtered and shown:

    [![Screenshot that shows how to see the Microsoft Edge Smart Screen policy settings in the settings catalog in Microsoft Intune.](media/tutorial-group-policy-migration/settings-catalog-microsoft-edge-smart-screen-filtered-settings.png)](media/tutorial-group-policy-migration/settings-catalog-microsoft-edge-smart-screen-filtered-settings.png#lightbox)

### Compare a policy in Group Policy Management and Intune

In this section, we show a policy in Intune and its matching policy in Group Policy Management Editor.

1. On the **Admin computer**, open the **Group Policy Management** app.

    This app gets installed with **RSAT: Group Policy Management Tools**, which is an optional feature you add on Windows. Prerequisites (in this article) lists the steps to install it.
2. Expand **Domains** &gt; select your domain. For example, select `contoso.net`.
3. Right-click the **OfficeandEdge** policy &gt; **Edit**. The Group Policy Management Editor app opens.

    ![Screenshot that shows how to right-click the on-premises Office and Microsoft Edge ADMX group policy, and select Edit.](media/tutorial-group-policy-migration/open-group-policy-management.png)

    **OfficeandEdge** is a group policy that includes the Office and Microsoft Edge ADMX templates. This policy is described in prerequisites (in this article).
4. Expand **Computer configuration** &gt; **Policies** &gt; **Administrative Templates** &gt; **Control Panel** &gt; **Personalization**. Notice the available settings.

    ![Screenshot that shows how to expand Computer Configuration in on-premises Group Policy Management Editor, and go to Personalization.](media/tutorial-group-policy-migration/open-group-policy-management-editor-admx-policy.png)

    Double-click **Prevent enabling lock screen camera**, and see the available options:

    ![Screenshot that shows how to see the on-premises Computer configuration setting options in group policy.](media/tutorial-group-policy-migration/prevent-enabling-lock-screen-camera-admx-policy.png)
5. In the Intune admin center, go to your **Windows student devices** settings catalog policy.
6. Select **Configuration settings** &gt; **Edit** &gt; **Add settings**. Search for **Personalization** and select the `Administrative templates\Control Panel\Personalization` category. Notice the available settings:

    [![Screenshot that shows the ADMX personalization policy setting path in the Microsoft Intune settings catalog.](media/tutorial-group-policy-migration/settings-catalog-admx-personalization-category.png)](media/tutorial-group-policy-migration/settings-catalog-admx-personalization-category.png#lightbox)

    This path and the available settings are similar to what you see in Group Policy Management Editor. If you select the **Prevent enabling lock screen camera** setting, you see similar options that are available in Group Policy Management Editor.

    [![Screenshot that shows the ADMX Prevent enabling lock screen camera setting path in the Microsoft Intune settings catalog.](media/tutorial-group-policy-migration/settings-catalog-control-panel-personalization.png)](media/tutorial-group-policy-migration/settings-catalog-control-panel-personalization.png#lightbox)

### Compare a user policy in Group Policy Management and Intune

1. In your **Windows student devices** settings catalog policy, select **Configuration settings** &gt; **Edit** &gt; **Add settings**. Search for `inprivate browsing`. Notice the settings options. The `(User)` setting applies to user configurations. The other setting applies to device configurations.

    [![Screenshot that shows a user setting and a device setting in the Microsoft Intune settings catalog.](media/tutorial-group-policy-migration/settings-catalog-inprivate-browsing.png)](media/tutorial-group-policy-migration/settings-catalog-inprivate-browsing.png#lightbox)
2. In **Group Policy Management Editor**, find the matching user and device settings:

    - Device: Expand **Computer configuration** &gt; **Policies** &gt; **Administrative Templates** &gt; **Windows components** &gt; **Internet Explorer** &gt; **Privacy** &gt; **Turn off InPrivate Browsing**.
    - User: Expand **User configuration** &gt; **Policies** &gt; **Administrative Templates** &gt; **Windows components** &gt; **Internet Explorer** &gt; **Privacy** &gt; **Turn off InPrivate Browsing**.

    ![Screenshot that shows how to turn off InPrivate Browsing in Internet Explorer using on-premises ADMX template.](media/tutorial-group-policy-migration/group-policy-turn-off-inprivate-browsing.png)

Tip

To see the built-in Windows policies, you can also use GPEdit (**Edit group policy** app).

### What did I just do?

You created a settings catalog policy in Intune. In this policy, we looked at some settings, and looked at the same ADMX settings in on-premises Group Policy Management.

## Create a OneDrive settings catalog policy

In this section, you create a OneDrive settings catalog policy in Intune to control some settings. These specific settings are chosen because they're commonly used by organizations.

1. Create another Intune policy (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**).
2. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Settings catalog**.
3. Select **Create**.
4. In **Basics**, enter the following properties:

    - **Name**: Enter **OneDrive policies for all Windows users**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
5. Select **Next**.
6. In **Configuration settings**, select **Add settings**. In the category list, search for or go to **OneDrive**. Select the following settings and then close the settings picker:

    - **Prevent users from syncing personal OneDrive accounts (User)**
    - **Silently sign in users to the OneDrive sync app with their Windows credentials**
    - **Use OneDrive Files On-Demand**
7. Configure these settings:

    | Setting | Value |
    | --- | --- |
    | Prevent users from syncing personal OneDrive accounts (User) | Enabled |
    | Silently sign in users to the OneDrive sync app with their Windows credentials | Enabled |
    | Use OneDrive Files On-Demand | Enabled |

Your settings look similar to the following settings:

![Screenshot that shows how to create a OneDrive settings catalog policy in Microsoft Intune.](media/tutorial-group-policy-migration/settings-catalog-onedrive.png)

For more information on OneDrive client settings, go to [Use Group Policy to control OneDrive sync client settings](/en-us/sharepoint/use-group-policy).

### Assign your policy

1. In your policy, select **Next** until you get to **Assignments**. Choose **Add groups**:
2. A list of existing users and groups is shown. Select the **All Windows devices** group you created earlier &gt; **Select**.

    If you're using this walkthrough in a production environment, then consider adding groups that are empty. The goal is to practice assigning your policy.
3. Select **Next**. In **Review + create**, select **Create** to save your changes.

In this section, you created some settings catalog policies, and assigned them to groups you created.

## Policy best practices

When you create policies and profiles in Intune, there are some recommendations and best practices to consider. For more information, go to [policy and profile best practices](../create-device-profile#recommendations).

## Clean up resources

When no longer needed, you can:

- Delete the groups you created:

    - **All Windows student devices**
    - **All Windows devices**
    - **All Teachers**
- Delete the settings catalog policies you created:

    - **Windows student devices**
    - **OneDrive policies that apply to all Windows users**

## Summary

In this tutorial, you got more familiar with the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), used the query builder to create dynamic groups, and created settings catalog policies in Intune to configure different settings. You also compared using ADMX templates on-premises and in the cloud with Intune.