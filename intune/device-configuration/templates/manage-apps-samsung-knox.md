---
layout: Conceptual
title: Allow or block apps for Samsung Knox Standard devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/manage-apps-samsung-knox
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
description: Create a custom profile to allow and block apps for Samsung Knox Standard Android device administrator devices using Microsoft Intune.
ms.date: 2025-02-18T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 0cf3d911-0218-db62-fe48-85ecb76b4d84
document_version_independent_id: 0cf3d911-0218-db62-fe48-85ecb76b4d84
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/manage-apps-samsung-knox.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/manage-apps-samsung-knox
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/manage-apps-samsung-knox.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 92fcf3d7-a01d-7201-7140-e10ab031606c
---

# Allow or block apps for Samsung Knox Standard devices - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Use the steps in this article to create a Microsoft Intune custom policy that creates one of the following lists:

- A list of apps that are blocked from running on the device. Apps in this list are blocked from being run, even if they were already installed when the policy was applied.
- A list of apps that users of the device are allowed to install from the Google Play store. Only the apps you list can be installed. No other apps can be installed from the store.

This feature applies to:

- Android device administrator (DA)

These settings are only used on devices that run Samsung Knox Standard.

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create an allowed or blocked app list

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Android device administrator**.
    - **Profile type**: Select **Custom**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android Samsung Knox - blocks apps**.
    - **Description**: Enter a description that gives an overview of the setting, and any other important details. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select **Add**. Enter the following custom OMA-URI settings:

    For a list of apps that are blocked from running on the device:

    - **Name**: Enter **PreventStartPackages**.
    - **Description**: Enter a description that gives an overview of the setting, and any other relevant information that can help you locate the profile. For example, enter **List of apps that are blocked from running**.
    - **OMA-URI** (case sensitive): Enter `./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages`.
    - **Data type**: Select **String**.
    - **Value**: Enter a list of the app package names you want to block. You can use `;`, `:`, or `|` as a delimiter. For example, enter `package1;package2;`.

    For a list of apps that users are allowed to install from the Google Play store while excluding all other apps:

    - **Name**: Enter **AllowInstallPackages**.
    - **Description**: Enter a description that gives an overview of the setting, and any other relevant information that can help you locate the profile. For example, enter **List of apps that users can install from Google Play**.
    - **OMA-URI** (case sensitive): Enter `./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages`.
    - **Data type**: Select **String**.
    - **Value**: Enter a list of the app package names you want to allow. You can use `;`, `:`, or `|` as a delimiter. For example, enter `package1;package2;`.
8. **Save** your changes and select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or device groups that will receive your profile. For more information on assigning profiles, go to [assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

Tip

You can find the package ID of an app by browsing to the app on the Google Play store. The package ID is contained in the URL of the app's page. For example, the package ID of the Microsoft Word app is `com.microsoft.office.word`.

The next time each targeted device checks in, the app settings are applied.