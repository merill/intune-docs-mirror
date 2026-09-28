---
layout: Conceptual
title: Require multifactor authentication for Intune device enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/configure-multifactor-authentication
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: How to require multifactor authentication in Microsoft Entra ID for Intune device enrollment.
ms.date: 2024-12-11T00:00:00.0000000Z
ms.topic: how-to
ROBOTS: 
ms.reviewer: damionw
locale: en-us
document_id: 51403232-1a28-ef6e-0616-9586493d0d81
document_version_independent_id: 51403232-1a28-ef6e-0616-9586493d0d81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/configure-multifactor-authentication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/configure-multifactor-authentication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/configure-multifactor-authentication.md
platformId: 6c990e44-b494-396a-c70c-218b0a715156
---

# Require multifactor authentication for Intune device enrollment - Microsoft Intune | Microsoft Learn

You can use Intune together with Microsoft Entra Conditional Access policies to require multifactor authentication (MFA) during device enrollment. If you require MFA, employees and students wanting to enroll devices must first authenticate with a second device and two forms of credentials. MFA requires them to authenticate using two or more of these verification methods:

- Something they know, such as a password or PIN.
- Something they have that can't be duplicated, such as a trusted device or phone.
- Something they are, such as a fingerprint.

If a device isn't compliant, the device user is prompted to make the device compliant before enrolling in Microsoft Intune.

## Requirements

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Multifactor authentication is available for the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - Windows
> 

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> To implement this policy, users must be assigned [Microsoft Entra ID P1 or later](/en-us/entra/fundamentals/licensing).

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Configure Intune to require multifactor authentication at device enrollment

Complete these steps to enable multifactor authentication during Microsoft Intune enrollment.

Important

Don't configure **Device based access rules** for Microsoft Intune enrollment.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Manage devices**, and then select **Conditional Access**. This Conditional Access area is the same as the Conditional Access area available in the Microsoft Entra admin center. For more information about the available settings, see [Building a Conditional Access policy](/en-us/entra/identity/conditional-access/concept-conditional-access-policies).
4. Choose **Create new policy**.
5. Name your policy.
6. Select the **Users** category.

    1. Under the **Include** tab, choose **Select users or groups**.
    2. Additional options appear. Select **Users and groups**. A list of users and groups opens.
    3. Browse and select the Microsoft Entra users or groups you want to include in the policy. Then choose **Select**.
    4. To exclude users or groups from the policy, select the **Exclude** tab and add those users or groups like you did in the previous step.
7. Select the next category, **Target resources**. In this step, you select the resources that the policy applies to. In this case, we want the policy to apply to events where users or groups try to access the Microsoft Intune Enrollment app.

    1. Under **Select what this policy applies to**, choose **Resources (formerly cloud apps)**.
    2. Select the **Include** tab.
    3. Choose **Select resources**. Additional options appear.
    4. Under **Select**, choose **None**. A list of resources open.
    5. Search for **Microsoft Intune Enrollment**. Then choose **Select** to add the app.

    For Apple automated device enrollments using Setup Assistant with modern authentication, you have two options to choose from. The following table describes the difference between the *Microsoft Intune* option and *Microsoft Intune Enrollment* option.

    | Cloud app | MFA prompt location | Automated Device Enrollment notes |
    | --- | --- | --- |
    | **Microsoft Intune** | Setup Assistant,Company Portal app | With this option, MFA is required during enrollment and each time the user signs into the Company Portal app or website. The MFA prompts appear on the Company Portal sign-in page. |
    | **Microsoft Intune Enrollment** | Setup Assistant | With this option, MFA is required during device enrollment and appears as a one-time MFA prompt on the Company Portal sign-in page. |

    Note

    The Microsoft Intune Enrollment cloud app isn't created automatically for new tenants. To add the app for new tenants, a Microsoft Entra administrator must create a service principal object, with app ID d4ebce55-015a-49b5-a083-c84d1797ae8c, in PowerShell or Microsoft Graph.
8. Select the **Grant** category. In this step, you grant or block access to the Microsoft Intune Enrollment app.

    1. Choose **Grant access**.
    2. Select **Require multifactor authentication**.
    3. Select **Require device to be marked as compliant**.
    4. Under **For multiple controls**, select **Require all the selected controls**.
    5. Choose **Select**.
9. Select the **Session** category. In this step, you can make use of session controls to enable limited experiences within the Microsoft Intune Enrollment app.

    1. Select **Sign-in frequency**. Additional options appear.
    2. Choose **Every time**.
    3. Choose **Select**.
10. For **Enable policy**, select **On**.
11. Select **Create** to save and create your policy.

After you apply and deploy this policy, device users enrolling their devices see a one-time MFA prompt.

Note

A second device or a Temporary Access Pass is required to complete the MFA challenge for these types of corporate-owned devices:

- Android Enterprise fully managed devices
- Android Enterprise corporate-owned devices with a work profile
- iOS/iPadOS devices enrolled via Apple automated device enrollment
- macOS devices enrolled via Apple automated device enrollment

The second device is required because the primary device can't receive calls or text messages during the provisioning process.