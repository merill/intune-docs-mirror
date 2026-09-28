---
layout: Conceptual
title: Create an Email Device Profile for iOS/iPadOS Devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/quickstart-email-profile
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
description: Learn how to create an email device profile in Microsoft Intune for iOS/iPadOS devices. Configure email settings to help users securely access organization email.
ms.date: 2026-01-20T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: 97eedd8b-aa6e-3089-5c06-8ca6e103af0c
document_version_independent_id: 97eedd8b-aa6e-3089-5c06-8ca6e103af0c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/quickstart-email-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/quickstart-email-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/quickstart-email-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f49a5507-1a31-0f6d-32cb-b2e65faa18d9
---

# Create an Email Device Profile for iOS/iPadOS Devices - Microsoft Intune | Microsoft Learn

In this article, you create an email profile for iOS/iPadOS devices. Email device profiles help standardize settings across your devices. By using these profiles, end users can access organization email on their personal devices without any confusing setup.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

To help safeguard your email, you can create a compliance policy that sets rules on devices that connect to email. Then, set up Conditional Access to allow only compliant devices access to your email profiles. To learn more about email profiles, see [configure email settings in Microsoft Intune](configure-email).

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** Microsoft Intune role
> 

## Create an iOS/iPadOS email profile

The profile includes the required settings that allow a device to connect to your organization's email.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**:

    [![Screenshot of Devices section in Intune admin center, Configuration selected, and Create button visible for new policy setup.](media/quickstart-email-profile/ios-create-profile.png)](media/quickstart-email-profile/ios-create-profile.png#lightbox)
3. Enter the following properties:

    - **Platform**: Select **iOS/iPadOS**.
    - **Profile type**: Select **Templates** &gt; **Email**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile. For this example, enter **iOS require work email**.
    - **Description**: Enter **Require iOS/iPadOS devices to use work email**.

    [![Screenshot of Microsoft Intune admin center, Basics step for iOS email profile with Name and Description entered.](media/quickstart-email-profile/ios-email-profile-name.png)](media/quickstart-email-profile/ios-email-profile-name.png#lightbox)
6. Select **Next**.
7. In **Configuration settings**, enter the following settings. For the other settings, use the default values.

    - **Email server**: For this evaluation step, enter `outlook.office365.com`. This setting specifies the Exchange location (URL) of the email server that the iOS/iPadOS mail app uses to connect to email.
    - **Account name**: Enter **Company Email**.
    - **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username for this profile using this name. For this evaluation step, use the **User Principal Name** as the username for the profile, like `user1@contoso.com`.
    - **Email address attribute from Microsoft Entra ID**: This setting is the email address from Microsoft Entra ID that signs in to Exchange. For this evaluation step, select **User Principal Name**.
    - **Authentication method**: For this evaluation step, select **Username and password**. If you set up [authentication certificates in Intune](../../fundamentals/certificates/overview), then you can choose **Certificate**.
8. Select **Next**.
9. In **Scope tags** (optional), select **Next**. In this example, don't use scope tags.
10. In **Assignments**, use the drop-down for **Assign to** and select **All users and all devices**. Then, select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned.

## Clean up resources

If you don't use this profile for other tutorials or testing, delete it:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices** &gt; **Configuration**.
2. Select the **iOS/iPadOS require work email** profile you created, and then select **Delete**.