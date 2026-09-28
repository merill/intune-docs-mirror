---
layout: Conceptual
title: Create a Password Compliance Policy for Android Enterprise - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/quickstart-password-compliance-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Android
- sub-device-compliance
ms.subservice: protect
description: Create a password compliance policy in Microsoft Intune for Android Enterprise devices. Learn to require specific password lengths to meet your organization's security requirements.
ms.date: 2026-01-15T00:00:00.0000000Z
ms.topic: article
ms.reviewer: andreibiswas
locale: en-us
document_id: f09efcca-dd5a-fe6b-7802-f1a2b034bef3
document_version_independent_id: f09efcca-dd5a-fe6b-7802-f1a2b034bef3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/quickstart-password-compliance-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/quickstart-password-compliance-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/quickstart-password-compliance-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c6c1ea09-085d-26f1-a1c8-5615e60e92cb
---

# Create a Password Compliance Policy for Android Enterprise - Microsoft Intune | Microsoft Learn

In this article, you use Microsoft Intune to create a password compliance policy for Android Enterprise devices. This policy requires your Android users to enter a password of a specific length to be compliant with your organization's security requirements. You can create a password compliance policy for any device platform that Intune supports. This example uses Android Enterprise.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

An Intune device compliance policy specifies the rules and settings that devices must meet to be considered compliant. You can enforce these compliance policies by using Microsoft Entra Conditional Access, which you can use to allow or block access to company resources. You can also get device reports and take actions for non-compliance.

Important

In addition to password settings, consider other system security settings to protect your workforce. For more information, see [System security settings](ref-android-enterprise-settings).

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Policy and Profile manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** Microsoft Intune role
> 

## Create a device compliance policy

Create a device compliance policy that requires your Android users to enter a password of a specific length.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** &gt; **Compliance**.
2. On the **Policies** tab, select **Create policy**.
3. For **Platform**, select **Android Enterprise**.
4. For **Profile type**, select either **Fully managed, dedicated, and corporate-owned work profile** or **Personally-owned work profile**, and then select **Create**.
5. On **Basics**, enter **Android compliance** as the *Name*. Adding a *Description* is optional. Select **Next**.
6. On **Compliance settings**, expand **System Security** and configure the following settings:

    - For **Require a password to unlock mobile devices**, select **Require**.
    - For **Required password type**, select **At least numeric**.
    - For **Minimum password length**, enter **6**.

    [![Screenshot of Microsoft Intune admin center showing Compliance settings for Android with password requirements highlighted.](media/quickstart-password-compliance-android/quickstart-set-password-length-android-01.png)](media/quickstart-password-compliance-android/quickstart-set-password-length-android-01.png#lightbox)
7. On the **Assignments**, you can optionally assign the policy to the user or group you created in [Step 2 - Create a user and assign a license](../../fundamentals/tenant-administration/quickstart-create-user) and [Step 3 - Create a group](../../fundamentals/tenant-administration/quickstart-create-group) evaluation steps.
8. When done, select **Next** until you reach the **Review + create** step. Then, select **Create** to create the policy.

When you successfully create the policy, it appears in your list of device compliance policies.

## Conditional Access policy assignment

With the free trial, you can create a Conditional Access policy that enforces this password requirement. This tutorial doesn't include these steps but you can do it.

For more information, see:

- [Learn about Conditional Access and Intune](../conditional-access-integration/overview)
- [Common ways to use Conditional Access with Intune](../conditional-access-integration/scenarios)

## Clean up resources

When you no longer need the policy, delete it. To delete the policy, select the compliance policy and select **Delete**.