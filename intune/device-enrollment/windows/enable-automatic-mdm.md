---
layout: Conceptual
title: Enable MDM automatic enrollment for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: maholdaa
ms.subservice: enrollment
description: Enable Intune automatic enrollment for Windows devices joining or registering with your Microsoft Entra ID.
ms.date: 2026-03-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 2b67a8a1-4468-b2f4-f7c9-20665d3fc0db
document_version_independent_id: 2b67a8a1-4468-b2f4-f7c9-20665d3fc0db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/enable-automatic-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/enable-automatic-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/enable-automatic-mdm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: fc9026e2-c0a4-0151-de0b-1e3aadc5b0f1
---

# Enable MDM automatic enrollment for Windows - Microsoft Intune | Microsoft Learn

Simplify device enrollment by enabling *automatic enrollment* in Microsoft Intune. This enrollment method enables devices to enroll automatically when they join or register in Microsoft Entra ID. Enrollment in Intune occurs when:

- A Microsoft Entra user adds their work or school account to their personal device.
- A corporate-owned device joins to your Microsoft Entra ID.

Automatic enrollment can be used in the following device management and provisioning scenarios:

- Bring-your-own-device (BYOD), personal devices
- Bulk enrollment
- Group Policy
- Windows Autopilot (user driven and self-deploying)
- Co-management with Configuration Manager

This article describes how to enable automatic mobile device management (MDM) enrollment for personal and corporate-owned devices.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> - [Microsoft Entra ID P1 or P2](/en-us/azure/active-directory/active-directory-get-started-premium) or the [Premium trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845). You can activate a free Premium trial subscription during setup.
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Global Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)** Microsoft Entra role
> 

## Enable Windows automatic enrollment

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Device onboarding** and select **Enrollment**.
4. Go to the **Windows** tab. Then select **Automatic Enrollment**.

    Note

    Automatic MDM enrollment is a premium Microsoft Entra feature available for Microsoft Entra ID Premium subscribers. If you can't see the automatic enrollment settings, select **Automatic MDM enrollment is available only for Microsoft Entra ID Premium subscribers** to activate a free trial.
5. Configure the **MDM user scope** for Microsoft Intune. This setting enables automatic MDM enrollment for Microsoft Entra users so that you can manage their devices in Intune.

![Screenshot shows the Microsoft Entra MDM user scope.](media/enable-automatic-mdm/auto-enroll-scope.png)

    Your options are:

    - **None** - Automatic MDM enrollment is disabled for all users. You can still manage devices in Microsoft Intune but users must initiate MDM enrollment.
    - **Some** - Automatic MDM enrollment is enabled for the users you select.
    - **All** - Automatic MDM enrollment is enabled for all users. Their devices automatically enroll in Intune when they join or register with Microsoft Entra ID.

    Tip

    If your intent is to enable automatic MDM enrollment for Windows BYOD devices, select **All** or **Some** for the MDM user scope. Then make sure the WIP user scope is **None** or **Some**, and that users are not members of both user scopes.
6. Use the default values for these URLs:

    - **MDM terms of use URL**
    - **MDM discovery URL**
    - **MDM compliance URL**
7. You have the option to control if users in an automatic enrollment configuration on Microsoft Entra registered devices are prompted to MDM enroll their device in the work or school account registration flow (referring to [Add Your Work or School Account to a Windows Device](https://support.microsoft.com/windows/add-your-work-or-school-account-to-a-windows-device-a6505ceb-1a20-4b15-889c-250175481506)). To control the behavior of the flow, use the **Disable MDM enrollment when adding work or school account** setting.

    Note

    This feature is in public preview.

    This setting is turned off by default. If you're enforcing Windows MAM for your work or school accounts, enable this setting. This setting applies to:

    - Users in the **Some** or **All** category in the MDM auto-enrollment configuration.
    - Users on Entra registered and workplace joined devices.
    - Users who add their account for the first time via Microsoft Edge or a native app such as Teams.

    This setting doesn't apply to users adding their account through the Settings flow.

    Note

    This setting only blocks the MDM enrollment option from users during the work or school account registration flow. Users can still MDM enroll their device through Windows Settings if they are in scope for MDM automatic enrollment, and through prompts they receive when they try to access a resource that requires MDM enrollment.
8. For **WIP user scope**, select **None**. If the WIP user scope is set to any other value, make sure the selected users aren't a part of the MDM user scope.

    Important

    When a user is in both the MDM user scope and WIP user scope:

    - The MDM user scope takes precedence if they're on a corporate-owned device. The device automatically enrolls in Microsoft Intune when they set it up for work.
    - The WIP user scope takes precedence if they bring their own device. The device doesn't enroll in Microsoft Intune for device management. Microsoft Purview Information Protection policies are applied if you configured them.
9. Select **Save**.

## Multifactor authentication

Two-factor authentication is not enabled for automatic enrollment by default. We recommend requiring multifactor authentication during device registration. For more information, see [Getting started with the Azure Multi-Factor Authentication Server](/en-us/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## Support for device users

The Microsoft Intune user help docs provide conceptual information, tutorials, and how-to guides for employees and students setting up their devices for work. You can point people directly to the Intune docs, or use these articles as guidance when developing and updating your own device management docs.

Users on personal devices running Windows can automatically enroll by adding their work or school account on their device, or by using the Intune Company Portal app. Devices running earlier versions of Windows must enroll using the Intune Company Portal app. For more information, see [Enroll Windows devices](../../user-help/enrollment/enroll-windows).

Intune also supports unlicensed admin access, which lets administrators sign in to the Intune admin center without an Intune license. Tenants created after July 2021 have this enabled by default. For more information, see [Unlicensed admins](../../fundamentals/licensing#unlicensed-admin-access).

## Best practices and troubleshooting

- Device users must access the Company Portal website through Microsoft Edge to view apps assigned for specific versions of Windows. Other browsers such as Google Chrome, Mozilla Firefox, and Internet Explorer do not support this type of filtering.
- After enrollment, you'll see two records in the Microsoft Intune admin center if automatic MDM enrollment is disabled and devices are joined to Microsoft Entra ID. To stop the duplicate records, instruct users on joined devices to **Settings** &gt; **Accounts** &gt; **Access work or school**. Then they can **Connect** using the same account.

## Known issues

There are no known issues in Microsoft Intune with MDM automatic enrollment for Windows.