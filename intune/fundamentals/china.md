---
layout: Conceptual
title: Intune operated by 21Vianet in China - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/china
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- government
ms.subservice: fundamentals
description: Intune operated by 21Vianet in China.
ms.date: 2025-10-16T00:00:00.0000000Z
ms.topic: article
ms.reviewer: amsaeedi, acabello
locale: en-us
document_id: c216c7a8-bcdd-7429-441b-d57c4b423eb3
document_version_independent_id: c216c7a8-bcdd-7429-441b-d57c4b423eb3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/china.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/china
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/china.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: e76b33b6-561b-a3ef-a324-61ff06a3c49c
---

# Intune operated by 21Vianet in China - Microsoft Intune | Microsoft Learn

Intune operated by 21Vianet is designed to meet the needs for secure, reliable, and scalable cloud services in China. Intune as a service is built on top of Microsoft Azure. Microsoft Azure operated by 21Vianet is a physically separated instance of cloud services located in China. It's independently operated and transacted by 21Vianet. This service is powered by technology that Microsoft has licensed to 21Vianet.

Microsoft doesn't operate the service itself. 21Vianet operates, provides, and manages delivery of the service. 21Vianet is an Internet data center services provider in China. It provides hosting, managed network services, and cloud computing infrastructure services. By licensing Microsoft technologies, 21Vianet operates local datacenters to provide you with the ability to use Intune service while keeping your data within China. 21Vianet also provides your subscription, billing, and support services.

Note

If you're interested in viewing or deleting personal data, see the [Azure Data Subject Requests for the GDPR](/en-us/microsoft-365/compliance/gdpr-dsr-azure) article. If you're looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## Feature differences in Intune operated by 21Vianet

Because the China services are operated by a partner from inside China, there are some feature differences with Intune.

- Intune operated by 21Vianet only supports standalone deployments. Customers can use co-management to attach their existing Configuration Manager deployment to the Microsoft Intune cloud.
- Migrations from public clouds to sovereign clouds aren't supported. Customers interested in moving to Intune operated by 21Vianet must migrate manually.
- The tenant attach feature (syncing devices to Intune without enrollment to support cloud console scenarios) isn't currently supported.
- Derived Credentials aren't supported with Intune operated by 21Vianet.
- Windows device management is supported using the modern MDM channel.
- Intune operated by 21Vianet doesn't support on-premises Exchange Connector.
- Intune operated by 21Vianet doesn't support [Microsoft Store for Business](/en-us/lifecycle/announcements/microsoft-store-for-business-education-retiring).
- [Windows Autopilot](/en-us/autopilot/overview) features, including Autopilot with co-management, aren't supported with Intune operated by 21Vianet. [Windows Autopilot Device Preparation](/en-us/autopilot/device-preparation/overview) is available on Intune operated by 21Vianet in China cloud.

    To learn more about the differences, see [Compare Autopilot solutions](/en-us/autopilot/device-preparation/compare).
- Intune operated by 21Vianet supports the Company Portal for Windows app. Use WinGet to download the Company portal package and dependencies and then deploy as a Line-of-Business app using Intune. [Use the WinGet tool to install and manage applications](/en-us/windows/package-manager/winget/).
- Microsoft Intune Endpoint Analytics and Log Analytics features aren't currently available.
- Azure Virtual Desktop Windows multi-session isn't currently supported for 21Vianet.
- Because Google Mobile Services isn't available in China, customers in Intune operated by 21Vianet can't use features that require Google Mobile Services. These features include:

    - Google Play Protect capabilities such as Play integrity verdict.
    - Managing apps from the Google Play Store.
    - Android Enterprise capabilities. For more information, see this [Google documentation](https://support.google.com/work/android/answer/6270910?hl=en).
- The Intune Company Portal app for Android uses Google Mobile Services (GMS) to communicate with the Microsoft Intune service. Because Google Play services isn't available in China, some tasks can require up to 8 hours to finish. For more information, see [Limitations of Intune management when GMS is unavailable](../app-management/manage-without-gms#limitations-of-intune-management-when-gms-is-unavailable).
- To follow local regulations and provide improved functionality, the Intune client experience (Company Portal app) may differ in China.
- Fencing isn't available.
- Mobile Application Management (MAM) availability is conditional on those apps being available in People's Republic of China.
- Mobile Threat Defense (MTD) connectors for Android and iOS/iPadOS devices are supported for the MTD partners that also support the 21Vianet environment. When you sign in to a 21Vianet tenant, you can see the connectors that are available in that environment.
- Intune operated by 21Vianet doesn't support Android (AOSP) management for corporate devices.
- Intune operated by 21Vianet doesn't support partner device management integration with Jamf for macOS devices.

## You control customer data

In Microsoft Azure, Intune, Microsoft 365, and Power BI operated by 21Vianet, you have full control of your data:

- You know where customer data is located.
- You control access to your customer data.
- You control your customer data if you leave the service.
- You have options to control the security of your customer data.

With Microsoft Azure, Intune, Microsoft 365, and Power BI operated by 21Vianet, you're the owner of your data:

- 21Vianet doesn't use customer data for advertising.
- You control who has access to your customer data.
- We use logical isolation to segregate each customer's data.
- We provide simple, transparent data-use policies, and get independent audits.
- Our subcontractors are under contract to meet our privacy requirements.

## Data subject requests

The Tenant Administrator role for Intune operated by 21Vianet can request data for data subjects in the following ways:

- In the Microsoft Entra admin center, a Tenant Administrator can permanently delete a data subject from Microsoft Entra ID and related services. For more information, see [Azure Data Subject Requests - Delete](/en-us/microsoft-365/compliance/gdpr-dsr-azure#step-5-delete)
- System-generated logs for Microsoft services operated by 21Vianet can be exported by Tenant Administrators using the Data Log Export. For more information, see [Azure Data Subject Requests - Export](/en-us/microsoft-365/compliance/gdpr-dsr-azure#step-6-export).