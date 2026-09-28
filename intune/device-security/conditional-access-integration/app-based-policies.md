---
layout: Conceptual
title: Use app-based Conditional Access policies with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- conditional-access
- sub-device-compliance
ms.reviewer: elocholi
ms.subservice: protect
description: Learn about using app-based Conditional Access policies with Microsoft Intune for both enrolled and unenrolled devices.
ms.date: 2023-09-18T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e826e6f4-3f16-2b7d-d3a0-9267278119e3
document_version_independent_id: e826e6f4-3f16-2b7d-d3a0-9267278119e3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/app-based-policies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/app-based-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/app-based-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 22dee6ae-35ec-7a29-71ec-29c8c5122d2f
---

# Use app-based Conditional Access policies with Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune app protection policies work with Microsoft Entra Conditional Access to help protect your organizational data on devices your employees use. These policies work on devices that enroll with Intune and on employee owned devices that don't enroll. Combined, they're referred to as app-based Conditional Access.

App-based Conditional Access with client app management adds a security layer that makes sure only client apps that support Intune app protection policies can access Exchange Online and other Microsoft 365 services.

Tip

In addition to app-based Conditional Access policies, you can use [device-based Conditional Access with Intune](device-based-policies).

## Requirements

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> Before you create an app-based Conditional Access policy, you must have a **Microsoft Entra ID P1 or P2** license. Users must also be licensed for Microsoft Entra ID. For more information, see [Microsoft Entra pricing](https://www.microsoft.com/security/business/microsoft-entra-pricing).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Your account must have one of the following roles in Microsoft Entra:
> 
> - Security administrator
> - Conditional Access administrator
> 

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> - Android
> - iOS/iPadOS
> 

## Supported apps

A list of apps that support app-based Conditional Access can be found in [Conditional Access: Conditions](/en-us/entra/identity/conditional-access/concept-conditional-access-conditions#client-apps) in the Microsoft Entra documentation.

App-based Conditional Access [also supports line-of-business (LOB) apps](block-no-modern-auth), but these apps need to use [Microsoft 365 modern authentication](/en-us/microsoft-365/enterprise/modern-auth-for-office-2013-and-2016?view=o365-worldwide&amp;preserve-view=true).

## How app-based Conditional Access works

App-based Conditional Access works by requiring a broker app to register the device with Microsoft Entra ID. The broker app can be Microsoft Authenticator on iOS, or Company Portal on Android. During authentication, Microsoft Entra ID checks whether the app is on the policy-approved list before granting access. The following diagram illustrates this process:

![App-based Conditional Access process illustrated in a flow-chart](media/app-based-policies/ca-intune-common-ways-3.png)

For a detailed technical overview, see [Client apps](/en-us/entra/identity/conditional-access/concept-conditional-access-conditions#client-apps) in the Microsoft Entra documentation.

## Create app-based Conditional Access policies

Conditional Access is a Microsoft Entra technology. The Conditional Access node you access from the Microsoft Intune admin center is the same node you access from Microsoft Entra ID, so you don't need to switch between them to configure policies.

Before you create Conditional Access policies, you need to have [Intune app protection policies](../../app-management/protection/create-policy) applied to your apps.

Important

This section walks through the steps to add a simple app-based Conditional Access policy. You can use the same steps for other cloud apps. For more information, see [Plan Conditional Access deployment](/en-us/entra/identity/conditional-access/plan-conditional-access).

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Conditional Access** &gt; **Create new policy**.
3. Enter a policy **Name**, and then under **Assignments**, configure **Users and groups** to apply the policy to users and groups. Use the **Include** or **Exclude** options to add your groups.
4. Under **Assignments**, configure **Target resources**. Apply the policy to **Cloud apps**. Use the **Include** or **Exclude** options to select the apps to protect. For example, choose **Select apps**, and select **Office 365**.
5. Select **Conditions** &gt; **Client apps** to apply the policy to apps and browsers. For example, select **Yes**, and then enable **Browser** and **Mobile apps and desktop clients**.
6. Under **Access controls**, configure **Grant**. For example, select **Grant access** &gt; **Require approved client app** and **Require app protection policy**, then select **Require one of the selected controls**.
7. Under **Enable policy**, select **On**, and then select **Create**.