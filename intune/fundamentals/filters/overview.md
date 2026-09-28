---
layout: Conceptual
title: Create assignment filters in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview
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
description: Create assignment filters in Microsoft Intune to target policies based on device properties like OS version or manufacturer. Learn to create, update, and delete filters for managed devices and apps.
ms.date: 2026-05-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mattcall
locale: en-us
document_id: 7d1cef77-ff8f-d886-77ca-fe4040b5cc35
document_version_independent_id: 7d1cef77-ff8f-d886-77ca-fe4040b5cc35
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/filters/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/filters/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/filters/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: efae12f1-b53a-c12b-1f84-4b720f44cae1
---

# Create assignment filters in Microsoft Intune - Microsoft Intune | Microsoft Learn

Assignment filters in Microsoft Intune let you assign policies based on rules you create. Use assignment filters to narrow policy scope by targeting devices with specific OS versions, manufacturers, or ownership types (personal vs. organization-owned). This targeting capability helps you apply the right policies to the right devices automatically.

Assignment filters are available for:

- Devices enrolled in Intune, which are **managed devices**.
- Apps that are managed by Intune, which are **managed apps**.

    Managed apps are used in mobile application management (MAM) scenarios. MAM involves managing apps on devices that aren't enrolled in Intune, which is common with personally owned devices. For more information on MAM in Intune, go to [What is Microsoft Intune app management?](../../app-management/overview).

Use assignment filters in the following scenarios:

- Deploy a Windows device restriction policy to only the corporate devices in the Marketing department, while excluding personal devices.
- Deploy an iOS/iPadOS app to only the iPad devices in the Finance users group.
- Deploy an Android mobile phone compliance policy to all users in the company, and exclude Android meeting room devices that don't support the mobile phone compliance policy settings.
- On personally owned devices, deploy an app configuration policy for a specific app manufacturer or an app protection policy that runs a specific OS version.

Assignment filters include the following features and benefits:

- Improve flexibility and granularity when assigning Intune policies and apps.
- Are used when assigning apps, policies, and profiles. They dynamically target managed devices based on device properties and target managed apps based on app properties you enter.
- Can include or exclude devices or apps in a specific group based on criteria you enter.
- Can create a query of device or app properties based on different properties, like device platform or application version.
- Can be used and reused in multiple scenarios in "Include" or "Exclude" mode.

This feature applies to:

- **Managed devices** on the following platforms:

    - Android device administrator
    - Android Enterprise
    - Android (AOSP)
    - iOS/iPadOS
    - macOS
    - Windows
- **Managed apps** on the following platforms:

    - Android
    - iOS/iPadOS
    - Windows

This article describes the assignment filter architecture, and shows you how to create, update, and delete an assignment filter.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## How assignment filters work

[![Screenshot that shows how an admin creates an assignment filter, and uses the assignment filter in a policy in Microsoft Intune.](media/overview/admin-creates-filter.png)](media/overview/admin-creates-filter.png#lightbox)

Before you apply a policy to an app or device, assignment filters dynamically evaluate applicability. Here's an overview of the image:

1. You create a reusable assignment filter based on an app or device property. In the example, the device filter is for iPhone XR devices.
2. You assign a policy to the group. In the assignment, you add the assignment filter in include or exclude mode. For example, you "include" iPhone XR devices, or you "exclude" iPhone XR devices from the policy.
3. The assignment filter is evaluated when the device enrolls, checks in with the Intune service, or at any other time a policy evaluates.
4. You see the assignment filter results based on the evaluation. For example, the app or policy applies, or it doesn't apply.

### Assignment filters vs. dynamic groups

If you're deciding between assignment filters and dynamic groups for device targeting, consider the following:

- **Use assignment filters** when you're targeting Intune policies or apps based on device properties (OS, model, manufacturer, ownership, category). Filters evaluate at check-in with no further evaluation delay.
- **Use dynamic groups** when you need cross-workload targeting (Conditional Access, licensing), Autopilot profile assignment, or user-based grouping.

Many organizations use both: dynamic groups for cross-workload scenarios and assignment filters for Intune-specific device targeting. For guidance on all available targeting methods, go to [Choose the right targeting method in Microsoft Intune](../choose-targeting-method).

Note

Because assignment filters don't require group membership processing, policy targeting isn't affected by group size, rule complexity, or membership evaluation timing. For performance recommendations when working with groups and filters, go to [Performance recommendations for grouping, targeting, and filtering in large Microsoft Intune environments](performance-recommendations).

### Restrictions

There are some general restrictions when creating assignment filters:

- You can have up to 200 assignment filters for each tenant.
- Each assignment filter is limited to 3,072 characters.
- For managed devices, the devices must be enrolled in Intune.
- For managed apps, assignment filters apply to app protection policies and app configuration policies. They don't apply to other policies, like compliance or device configuration profiles.

## Prerequisites

- Sign in as an Intune administrator. For more information on Intune roles, go to [Role-based access control (RBAC) with Microsoft Intune](../role-based-access-control/overview).

## Create a filter

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Assignment filters** &gt; **Create**.

    You can also create assignment filters in:

    - **Devices** &gt; **Organize devices** &gt; **Assignment filters**
    - **Apps** &gt; **Organize devices** &gt; **Assignment filters**
3. Select **Managed devices** or **Managed apps**:

    ![Screenshot that shows selecting Managed apps or Managed devices when creating a filter in the Microsoft Intune admin center.](media/overview/managed-apps-managed-devices.png)

    Remember, managed devices are devices enrolled in Intune and are typically owned by the organizations. Managed apps are for devices that aren't enrolled in Intune and are typically owned by end users.
4. In **Basics**, enter the following properties:

    - **Filter name**: Enter a descriptive name for the assignment filter. Name your assignment filters so you can easily identify them later. For example, a good filter name is **Windows OS version filter**.
    - **Description**: Enter a description for the assignment filter. This setting is optional, but recommended.
    - **Platform**: Select your platform. Your options:

        - **Managed devices**:

            - Android device administrator
            - Android Enterprise
            - Android (AOSP)
            - iOS/iPadOS
            - macOS
            - Windows 10 and later
        - **Managed apps**:

            - Android
            - iOS/iPadOS
            - Windows
5. Select **Next**.
6. In **Rules**, there are two ways to create a rule: Use the **rule builder**, or use the **rule syntax**.

    **Rule builder**:

    - **And/Or**: After you add an expression, you can add to the expression using the `and` or `or` options.
    - **Property**: Select a property for your rule, like device or operating system SKU.
    - **Operator**: Select the operator from the list, like `equals` or `contains`.
    - **Value**: Enter the value in your expression. For example, enter `10.0.18362` for the OS version, or `Microsoft` for the manufacturer.
    - **Add expression**: After you add the property, operator, and value, select **Add expression**:

        ![Screenshot that shows how to use the rule builder in Microsoft Intune to create an expression assignment filter, and assign to your policies.](media/overview/rule-builder-example.png)

        The expression you created is automatically added to the rule syntax editor.

    **Rule syntax**:

    You can also manually enter your rule expression, and write your own rules in the rule syntax editor. In **Rule syntax**, select **Edit**:

    ![Screenshot that shows how to select rule syntax editor to use the rule builder in Microsoft Intune.](media/overview/rule-syntax-edit.png)

    The expression builder opens. Manually enter expressions, like `(device.osVersion -eq "10.0.18362") and (device.manufacturer -eq "Microsoft")`:

    ![Screenshot that shows how to use the expression builder to enter your rule syntax in Microsoft Intune.](media/overview/rule-syntax-example.png)

    For more information on writing your own expressions, see [Device and app properties, operators, and rule editing when creating assignment filters](ref-device-properties).

    Select **OK** to save your expression.

    Tip

    - When you create a rule, the system validates it for the correct syntax and shows any errors.
    - If you enter syntax that's not supported by the basic rule builder, then the rule builder is disabled. For example, using nested parenthesis disables the basic rule builder.
7. Select **Preview devices**. A list of enrolled devices that match your assignment filter criteria is shown.

    In this list, you can also search for devices by the device name, OS version, device model, device manufacturer, and more:

    ![Screenshot that shows how to search for devices when creating an assignment filter in Microsoft Intune.](media/overview/preview-search.png)

    Note

    When you select **Preview devices** for a property that's in preview, you get a `You cannot use Filter preview with experimental properties` message. Even though you can't preview the property, you can continue to use the property in your assignment filters.

    ![Screenshot that shows cannot use filter preview message when clicking Preview devices with a preview property in assignment filter rule syntax in Microsoft Intune.](media/overview/filter-preview.png)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../role-based-access-control/scope-tags).

    Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, your changes are saved. The assignment filter is created and ready to be used. The assignment filter is also shown in the assignment filters list.

## Use a filter

After the assignment filter is created, it's ready to use when assigning your apps or policies.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to your apps, compliance policies, or configuration profiles. For a list of supported workloads, see [Supported workloads when creating assignment filters](ref-supported-workloads). Select an existing policy, or create a new policy.

    For example, select **Devices** &gt; **Compliance**, and select an existing policy. Select **Properties** &gt; **Assignments** &gt; **Edit**:

    ![Screenshot that shows how to select a policy or profile, and edit the assignment in Microsoft Intune.](media/overview/edit-compliance-policy-assignment.png)
2. Assign your policy to a users group or a devices group.
3. Select **Edit filter**. Your options:

    - **Do not apply a filter**: All targeted users or devices receive the app or policy without filtering.
    - **Include filtered devices in assignment**: Devices that match the assignment filter conditions receive the app or policy. Devices that don't match the assignment filter conditions don't receive the app or policy.

        A list of assignment filters that match the policy platform is shown.
    - **Exclude filtered devices in assignment**: Devices that match the assignment filter conditions don't receive the app or policy. Devices that don't match the assignment filter conditions receive the app or policy.

        A list of assignment filters that match the policy platform is shown.
4. Select your existing assignment filter &gt; **Select**.

    For example, select **Include filtered devices in assignment**, and select the assignment filter:

    ![Screenshot that shows how to include the assignment filter when assigning a policy in Microsoft Intune.](media/overview/add-filter-compliance-policy.png)
5. To save your changes, select **Review + save** &gt; **Save**.

When the device checks in with the Intune service, the properties defined in the assignment filter are evaluated, and determine if the app or policy should be applied.

## Filter your existing assignment filters

After you create an assignment filter, you can filter the existing list of assignment filters by platform and by profile type (**Managed devices** or **Managed apps**).

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Assignment filters**. You see a list of all the assignment filters.

    You can also go to **Devices** &gt; **Organize devices** &gt; **Assignment filters**, or **Apps** &gt; **Assignment filters**.
2. Select **Add filters**:

    ![Screenshot that shows how to add a filter to filter the existing assignment filter list in Microsoft Intune.](media/overview/add-filter.png)
3. You can filter the list by the **Filter type** or by **Platform**:

    ![Screenshot that shows to filter the existing assignment filter list by platform and profile type in Microsoft Intune.](media/overview/add-filter-profile-type-platform.png)
4. Select **Filter type** &gt; **Apply**. Then select **Managed devices** or **Managed apps** &gt; **Apply**. The list of assignment filters is filtered based on your selection.

    ![Screenshot that shows the filtered list of assignment filters by managed devices in Microsoft Intune.](media/overview/filter-type-managed-devices.png)
5. Add another filter, select **Platform** &gt; **Apply**. Select your platform from the list, like **Windows 10 and later** &gt; **Apply**. The list of assignment filters is filtered based on your selection.

    ![Screenshot that shows the filtered list of assignment filters by platform in Microsoft Intune.](media/overview/filter-platform.png)

    ![Screenshot that shows the filtered list of assignment filters and all the available platform options in Microsoft Intune.](media/overview/filter-platform-list.png)

## Review the assignments

After you assign the assignment filter to your policies, you can see all the policies that use the assignment filter.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Assignment filters**. You see a list of all the assignment filters.

    You can also go to **Devices** &gt; **Organize devices** &gt; **Assignment filters**, or **Apps** &gt; **Assignment filters**.
2. Select the assignment filter you want to review &gt; **Associated Assignments** tab.

    The page shows all the apps and policies that use the assignment filter, the groups that receive the filter assignments, and the assignment filter mode (**Include** or **Exclude**):

    ![Screenshot that shows associated assignment tabs for an existing assignment filter in Microsoft Intune.](media/overview/associated-assignments-filter-mode.png)

## Change an existing filter

After you create an assignment filter, you can change or update it.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Assignment filters**. You see a list of all the assignment filters.

    You can also update assignment filters in **Devices** &gt; **Organize devices** &gt; **Assignment filters**, or **Apps** &gt; **Assignment filters**.
2. To update an existing assignment filter, select the assignment filter you want to change. Select **Rules** &gt; **Edit**, and make your changes:

    ![Screenshot that shows how to change or update an existing assignment filter in Microsoft Intune.](media/overview/update-existing-filter.png)
3. To save your changes, select **Review + save** &gt; **Save**.

## Delete a filter

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Assignment filters**. You see a list of all the assignment filters.

    You can also delete assignment filters in **Devices** &gt; **Organize devices** &gt; **Assignment filters**, or **Apps** &gt; **Assignment filters**.
2. Next to the assignment filter, select the ellipses (**...**), and select **Delete**:

    ![Screenshot that shows how to delete an assignment filter in Microsoft Intune.](media/overview/delete-filter.png)

    To delete an assignment filter, you must remove the assignment filter from any policy assignments. Otherwise, when you try to delete the assignment filter, the following error is shown:

    `Unable to delete assignment filter – An assignment filter is associated with existing assignments. Delete all the assignments for the filter and try again.`