---
layout: Conceptual
title: Deploy Microsoft Edge policy using settings catalog in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-edge
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
description: Add or create settings using the settings catalog to configure Microsoft Edge on Windows and macOS devices. Using Microsoft Intune, you can configure group policy settings, and deploy these settings to Microsoft Edge users.
ms.date: 2026-04-30T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mayurjadhav
locale: en-us
document_id: 8af7ab3c-32a7-cf1c-2161-265b09f58ab2
document_version_independent_id: 8af7ab3c-32a7-cf1c-2161-265b09f58ab2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/configure-edge.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/configure-edge
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/configure-edge.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 81dc67bd-2ccc-94f6-2dd1-9b8ab6b05fce
---

# Deploy Microsoft Edge policy using settings catalog in Microsoft Intune - Microsoft Intune | Microsoft Learn

Using the [settings catalog](./) in Microsoft Intune, you can create and manage Microsoft Edge policy settings on your Windows and macOS devices. The Microsoft Edge settings are ADMX-backed policy settings, similar to on-premises Group Policy Objects (GPO).

With these settings, you can control how Microsoft Edge works and configure Microsoft Edge features for users in your organization. For example, you can:

- Allow specific extensions
- Add download restrictions
- Use autofill
- Show the favorites bar
- And more...

These settings are created in an Intune policy, and then deployed to devices in your organization.

This article shows you how to configure Microsoft Edge policy settings using the [settings catalog](./) in Microsoft Intune.

This article applies to:

- Windows
- macOS
- Microsoft Edge version 77 and newer

    For Microsoft Edge version 45 and earlier, go to [Microsoft Edge Browser device restrictions](../templates/ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older).

Tip

- For information on adding the Microsoft Edge version 77+ app on Windows client, go to [Add Microsoft Edge app on Windows client devices](../../app-management/deployment/add-edge-windows).
- For information on adding and configuring Microsoft Edge version 77+ app on macOS, go to [Add Microsoft Edge app](../../app-management/deployment/add-edge-macos), and [Configure Microsoft Edge app using plist](/en-us/DeployEdge/configure-microsoft-edge-on-mac).
- For a list of the Microsoft Edge updates, including new policies, go to the [Release notes for Microsoft Edge](/en-us/deployedge/microsoft-edge-relnote-stable-channel#policy-updates).

## Prerequisites

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure the settings catalog policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile Manager** role. For more information on the built-in roles in Intune, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create a policy for Microsoft Edge

This section shows you how to create, search, and configure Microsoft Edge settings using the settings catalog.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **macOS** or **Windows 10 and later**.
    - **Profile type**: Select **Settings catalog**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Edge on Windows client devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select **Add settings**, and search for Edge:

    [![Screenshot that shows Microsoft Edge settings in the settings catalog in Microsoft Intune and Intune admin center.](media/configure-edge/settings-catalog-search-edge.png)](media/configure-edge/settings-catalog-search-edge.png#lightbox)

    Select the **Microsoft Edge** category. The settings with `(User)` in the name apply to all users signed in to the device. The other settings apply to the device, even if no one is signed in.

    [![Screenshot that shows Microsoft Edge user and device settings in the settings catalog in Microsoft Intune and Intune admin center.](media/configure-edge/settings-catalog-edge-user-device.png)](media/configure-edge/settings-catalog-edge-user-device.png#lightbox)
8. In search, find a specific Microsoft Edge setting you want to configure. For example, search for `home page`, and select the **Configure the home page URL** setting:

    [![Screenshot that shows home page URL settings in the settings catalog in Microsoft Intune and Intune admin center.](media/configure-edge/settings-catalog-edge-home-page-url.png)](media/configure-edge/settings-catalog-edge-home-page-url.png#lightbox)

    Note

    For a list of the available settings, go to [Microsoft Edge – Policies](/en-us/DeployEdge/microsoft-edge-policies) and [Microsoft Edge – Update policies](/en-us/DeployEdge/microsoft-edge-update-policies).
9. Close the settings picker. Set the **Configure the home page URL** setting to **Enabled**, and set its value to a URL, like `https://www.bing.com`:

    [![Screenshot of the Microsoft Edge home page URL set to a web site using the settings catalog in Microsoft Intune and Intune admin center.](media/configure-edge/settings-catalog-edge-home-page-url-enabled.png)](media/configure-edge/settings-catalog-edge-home-page-url-enabled.png#lightbox)
10. Select **Next**. In **Scope tags**, select **Next**.

    Scope tags are optional, and this example doesn't use them. To learn more about scope tags, and what they do, go to [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
11. In **Assignments**, select **Next**.

    Assignments are optional, and this example doesn't use them. In production, select **Add groups**. Select a Microsoft Entra group that includes users or devices that should receive this policy. For information and guidance on assigning policies, go to [Assign user and device profiles in Intune](../assign-device-profile).

    [![Screenshot of Assign or deploy the ADMX policy template to users or groups in Microsoft Intune and Intune admin center.](media/configure-edge/add-entra-group-assign-policy.png)](media/configure-edge/add-entra-group-assign-policy.png#lightbox)
12. In **Review + create**, the summary of your changes is shown. Select **Create**.

    When you create the profile, your policy is automatically assigned to the users or groups you chose. If you didn't choose any users or groups, then your policy is created, but it isn't deployed.

    In **Devices** &gt; **Configuration**, your new Microsoft Edge policy is shown in the list.