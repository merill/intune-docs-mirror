---
layout: Conceptual
title: Use Conditional Access with Microsoft Intune compliance policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview
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
description: Combine Conditional Access with Intune compliance policies to define the requirements that users and devices must meet before gaining access to your organization's resources.
ms.date: 2024-04-25T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: fc0740f6-07ab-a8b2-3219-373739fdc28f
document_version_independent_id: fc0740f6-07ab-a8b2-3219-373739fdc28f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: e32380e8-0b8e-16e1-4e08-cd83f5148b42
---

# Use Conditional Access with Microsoft Intune compliance policies - Microsoft Intune | Microsoft Learn

Use Conditional Access with Microsoft Intune compliance policies to control the devices and apps that can connect to your email and company resources. When integrated, you can gate access to keep your corporate data secure, while giving users an experience that allows them to do their best work from any device, and from any location.

[Conditional Access](/en-us/entra/identity/conditional-access/overview) is a Microsoft Entra capability that is included with a Microsoft Entra ID P1 or P2 license. Through Microsoft Entra ID, Conditional Access brings signals together to make decisions, and enforce organizational policies. Intune enhances this capability by adding mobile device compliance and mobile app management data as signals for Conditional Access decisions. For a full list of supported signals, see [What is Conditional Access?](/en-us/entra/identity/conditional-access/overview) in the Microsoft Entra documentation.

You configure Conditional Access policies from the Microsoft Intune admin center. The Conditional Access node in the Microsoft Intune admin center is the same node as in Microsoft Entra ID, so you don't need to switch between them.

![Conceptual Conditional Access process flow.](media/scenarios/ca-diagram-1.png)

Note

Conditional Access also extends its capabilities to [Microsoft 365 services](/en-us/office365/enterprise/office-365-client-support-conditional-access).

## Ways to use Conditional Access with Intune

Conditional Access works with Intune device configuration and compliance policies, and with Intune app protection policies.

- **Device-based Conditional Access**

    Intune and Microsoft Entra ID work together to make sure only managed and compliant devices can access email, Microsoft 365 services, software as a service (SaaS) apps, and on-premises apps.

    Learn more about [device-based Conditional Access with Intune](device-based-policies).
- **App-based Conditional Access**

    Intune and Microsoft Entra ID work together to make sure only managed apps can access corporate email or other Microsoft 365 services.

    Learn more about [app-based Conditional Access with Intune](app-based-policies).

## Known limitations

The compliant network location condition is only supported for devices enrolled in mobile device management (MDM). If you configure a Conditional Access policy using the compliant network location condition, users with devices that aren't yet MDM-enrolled might be affected. Users on these devices might fail the Conditional Access policy check, and be blocked. Ensure that you exclude the affected users or devices when using the compliant network location condition.