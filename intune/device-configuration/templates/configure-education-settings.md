---
layout: Conceptual
title: Add or configure education settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-education-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use the Take a Test app in a device configuration profile on Windows devices in Microsoft Intune. Create a configuration profile using the Education settings, and enter a test app URL, choose how users sign-in, monitor the screen during the test, and allow or prevent text suggestions during the test.
ms.date: 2026-06-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: heenamac
locale: en-us
document_id: b629c4fa-4de0-6e9f-32ef-7be1822085b5
document_version_independent_id: b629c4fa-4de0-6e9f-32ef-7be1822085b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-education-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-education-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-education-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 8d758256-75ce-438e-4609-cf373a141673
---

# Add or configure education settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Education profiles in Intune are designed for students to take a test or exam on devices. This feature includes the **Take a Test** app.

The Take a Test app lets you securely administer online tests on your classroom's Windows devices. To set up the Take a Test app, you create a device configuration profile in Intune and configure the secure assessment settings.

After you configure the profile, assign and deploy it to your students.

When the student signs in, the Take a Test app automatically opens with the test you entered. No other apps can run on the device while the test is in progress. [Take tests in Windows](/en-us/education/windows/take-tests-in-windows) provides more details on the Take a Test app.

This article lists the steps to create a device configuration profile in Microsoft Intune. It also lists and describes the available settings for your Windows devices.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure this policy and start collecting inventory data from devices, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

## Create a device profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Secure assessment (Education)**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, enter the settings you want to configure:

    - **Account type**: Choose how users sign in to the test. Your options:
        - Azure AD account (Microsoft Entra account)
        - Domain account
        - Local account
        - Local guest account
    - **Account user name**: Enter the user name of the account used with the Take a Test app. You can enter accounts in the following format:
        - `user@contoso.com`
        - `domain\username`
        - `user@contoso.com`
        - `computerName\username`
    - **Account name**: To set up a local guest account type, enter the name of the account used with the Take a Test app. The account name will appear as a tile on the sign-in screen. Students click the tile to launch the test.​
    - **Assessment URL**: Enter the URL of the test you want users to take. For more information on getting the URL, see the [Take a Test documentation](/en-us/education/windows/take-tests-in-windows).
    - **Printer connection**: **Require** only allows access to the Take a Test app from devices that are connected to a printer. This setting also makes the app's print button available to test-takers. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS may allow students to access the app from devices that aren't connected to a printer.​
    - **Screen monitoring**: **Allow** monitors the screen activity while users are taking a test. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS may prevent you from monitoring the screen during the test.
    - **Text suggestions**: Choose **Allow** so test takers can see text suggestions. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS may block text suggestions while users are taking a test.
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or user group that will receive your profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.