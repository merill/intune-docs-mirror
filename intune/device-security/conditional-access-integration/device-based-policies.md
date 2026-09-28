---
layout: Conceptual
title: Set up device-based Conditional Access policies with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/device-based-policies
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
ms.reviewer: ilwu
ms.subservice: protect
description: Configure a device-based Conditional Access policy that uses device compliance status from Intune device compliance policies.
ms.date: 2023-09-18T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c87b001a-6774-d3c1-0834-f5e05c990441
document_version_independent_id: c87b001a-6774-d3c1-0834-f5e05c990441
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/device-based-policies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/device-based-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/device-based-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: dda6fa1a-abc4-dbdb-5d75-202d6f14ec51
---

# Set up device-based Conditional Access policies with Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune device compliance policies can evaluate the status of managed devices to ensure they meet your requirements before you grant them access to your organization's apps and services. The status results from your device compliance policies can be used by Microsoft Entra Conditional Access policies to enforce security and compliance standards. This combination is referred to as device-based Conditional Access.

Tip

In addition to device-based Conditional Access policies, you can use [App-based Conditional Access with Intune](app-based-policies).

Conditional Access is a Microsoft Entra technology. The Conditional Access node you access from the Microsoft Intune admin center is the same node you access from Microsoft Entra ID, so you don't need to switch between them to configure policies.

## Requirements

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> Before you create a device-based Conditional Access policy, you must have a **Microsoft Entra ID P1 or P2** license. For more information, see [Microsoft Entra pricing](https://www.microsoft.com/security/business/microsoft-entra-pricing).

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Your account must have one of the following roles in Microsoft Entra:
> 
> - Security administrator
> - Conditional Access administrator
> 

Important

Before you set up Conditional Access, you'll need to set up Intune device compliance policies to evaluate devices based on whether they meet specific requirements. See [Get started with device compliance policies in Intune](../compliance/create-policy).

## How this works

Device-based Conditional Access uses compliance status signals from Intune to enforce access controls in Microsoft Entra ID. Configuration involves two phases:

- Phase 1 - Configure device compliance policies in Intune: These policies evaluate whether managed devices meet your security requirements. Intune reports that compliance status to Microsoft Entra ID.
- Phase 2 - Create a Conditional Access policy in Microsoft Entra: The policy uses the compliance signal from Intune. This article shows you how to configure the policy from within the Microsoft Intune admin center.

## Create the Conditional Access policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Conditional Access** &gt; **Create new policy**.

    The **New** pane opens, which is the configuration pane from Microsoft Entra. The policy you’re creating is a Microsoft Entra policy for Conditional Access. To learn more about this pane and Conditional Access policies, see [Conditional Access policy components](/en-us/entra/identity/conditional-access/concept-conditional-access-policies) in the Microsoft Entra content.
3. Under **Assignments**, configure **Users and groups** to select the Identities in the directory that the policy applies to. To learn more, see [Users and groups](/en-us/entra/identity/conditional-access/concept-conditional-access-users-groups) in the Microsoft Entra documentation.

    - On the **Include** tab, configure the user and groups you want to include.
    - Use the **Exclude** tab if there are any users, roles, or groups you want to exclude from this policy.

    Tip

    Test the policy against a smaller group of users to make sure it works as expected before deploying it to larger groups.
4. Next configure **Target resources**, which is also under *Assignments*. Use the drop-down for *Select what this policy applies to* to select **Cloud apps**.

    - On the **Include** tab, use available options to identify the apps and services that you want to protect with this Conditional Access policy.

        If you choose **Select apps**, use the available UI to select apps and services to protect with this policy.

Caution

**Don't lock yourself out**. If you choose **All cloud apps**, be sure to review the warning, and then **Exclude** from this policy your user account or other relevant users and groups that should retain access to use the Microsoft Entra admin center or Microsoft Intune admin center after this policy takes effect.
    - Use the **Exclude** tab if there are any apps or services you want to exclude from this policy.

    For more information, see [Cloud apps or actions](/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps) in the Microsoft Entra documentation.
5. Next, configure **Conditions**. Select the signals you want to use as conditions for this policy. Options include:

    - User risk
    - Sign-in risk
    - Device platforms
    - Locations
    - Client apps
    - Filter for devices

    For information about these options, see [Conditions](/en-us/entra/identity/conditional-access/concept-conditional-access-conditions) in the Microsoft Entra documentation.

    Tip

    If you want to protect both **Modern authentication** clients and **Exchange ActiveSync clients**, create two separate Conditional Access policies, one for each client type. Although Exchange ActiveSync supports modern authentication, the only condition that is supported by Exchange ActiveSync is platform. Other conditions, including multifactor authentication, aren't supported. To effectively protect access to Exchange Online from Exchange ActiveSync, create a Conditional Access policy that specifies the cloud app Microsoft 365 Exchange Online and the client app Exchange ActiveSync with Apply policy only to supported platforms selected.
6. Under **Access controls**, configure **Grant** to select one or more requirements. To learn about the options for Grant, see [Grant](/en-us/entra/identity/conditional-access/concept-conditional-access-grant) in the Microsoft Entra Documentation.

    Important

    To have this policy use device compliance status, for *Grant access* you must select *Require device to be marked as compliant*.

    - **Block access**: Denies access to the specified apps or services.
    - **Grant access**: Grants access, but you can require one or more conditions. To use device compliance status from Intune, select **Require device to be marked as compliant**.
7. Under **Enable policy**, select **On**. By default, the policy is set to *Report-only*.
8. Select **Create**.