---
layout: Conceptual
title: What are cloud-native Windows endpoints - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.reviewer: ahamil, jasandys, wicale
description: Learn more about cloud-native endpoints and what they are. See a list of benefits, and the effect on end users and IT administrators. Cloud-native endpoints help with remote workers and hybrid workers, and use Microsoft Intune to manage devices.
ms.date: 2026-05-28T00:00:00.0000000Z
ms.topic: overview
ms.keywords: cloud native Windows, cloud-native Windows endpoint, Intune cloud native, Windows Autopilot cloud native, cloud native endpoint setup
ms.collection:
- M365-identity-device-management
- highseo
- intune-scenario
locale: en-us
document_id: 8906b72a-a715-938e-40f4-6ef51ae8a36d
document_version_independent_id: 8906b72a-a715-938e-40f4-6ef51ae8a36d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/cloud-native-endpoints/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/cloud-native-endpoints/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/cloud-native-endpoints/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 79f997d3-2f99-ca2e-8f51-623d1e4117a8
---

# What are cloud-native Windows endpoints - Microsoft Intune | Microsoft Learn

Tip

When reading about cloud native endpoints, you see the following terms:

- **Endpoint**: An endpoint is a device, like a mobile phone, tablet, laptop, or desktop computer. "Endpoints" and "devices" are used interchangeably.
- **Managed endpoints**: Endpoints that receive policies from the organization using an MDM solution or Group Policy Objects. These devices are typically organization owned, but can also be BYOD or personally owned devices.
- **Cloud native endpoints**: Endpoints that are joined to Microsoft Entra. They aren't joined to on-premises AD.
- **Workload**: Any program, service, or process.

Organizations are focusing on supporting remote and hybrid workers. With cloud-native endpoints, organizations can:

- Ship devices directly to users.
- Automatically configure apps and settings on devices using an internet connection.
- Have users reset their devices and redeploy apps without losing data.
- Allow users to be productive from anywhere, while protecting and securing user and organization data.

In this set of articles, you will:

- ![](../../media/icons/16/check.svg)**Learn about cloud-native endpoints** and the benefits to organizations and end users (this article).
- ![](../../media/icons/16/check.svg)**Step through a tutorial** that creates a Windows device that's cloud-native:

    - [Tutorial: Set up cloud-native Windows endpoints with Microsoft Intune](tutorial-cloud-native-setup)
- ![](../../media/icons/16/check.svg)**Learn more about the Microsoft Entra concepts** that are part of cloud-native endpoints, including accessing on-premises resources:

    - [Entra joined vs. Hybrid Entra joined](entra-join-types)
    - [Cloud-native endpoints and on-premises resources](on-premises-resources)
- ![](../../media/icons/16/check.svg)**Get guidance and advice** on moving your workloads and your organization to become cloud-native:

    - [High level planning guide to move to cloud-native endpoints](planning-guide)
- ![](../../media/icons/16/check.svg)**Read about some scenarios** that can affect your cloud-native migration:

    - [Known issues and important information](troubleshoot)

## What are cloud-native endpoints

Cloud-native endpoints are devices that can be deployed from anywhere. They receive their applications and configurations dynamically from the cloud, and can easily be reset or restored.

A cloud-native endpoint doesn't necessarily live exclusively in the cloud. Instead, any endpoint that's cloud-native eliminates hard dependencies to on-premises connectivity and on-premises resources.

These endpoints can be located anywhere that has internet access. They can also be physical devices or virtual machines.

From a technical perspective, cloud-native endpoints are Windows devices that are deployed using [Windows Autopilot](/en-us/autopilot/overview), joined to Microsoft Entra ([Microsoft Entra joined devices](/en-us/entra/identity/devices/concept-directory-join)), and are automatically enrolled in a Mobile Device Management (MDM) solution, like [Microsoft Intune](../../fundamentals/what-is-intune).

A cloud-native endpoint has the following characteristics:

- Provisioned and managed from cloud-based services
- Can use and access other cloud-based endpoints from anywhere
- Microsoft Entra joined
- Includes configuration, data, and applications that are portable and roam with the user
- Doesn't generally require a direct connection to any on-premises resources for usability or management

For end users, they only need an internet connection. Their data and critical settings can be automatically preserved and restored using [Enterprise State Roaming](/en-us/entra/identity/devices/enterprise-state-roaming-faqs), or similar solutions. If end users experience issues during deployment or at any time, then they can reset and reprovision the device without contacting support.

Microsoft recommends that organizations focus on adopting cloud-native endpoints.

## Benefits for users and IT

Cloud-native endpoints provide many benefits to end users and IT:

- **Best for remote workers**

    End users don't worry about connecting to the VPN or other networks. They sign in to devices from anywhere, and run actions, like password reset, without connecting to on-premises AD.

    Microsoft Entra joined endpoints do the initial sign-in using an internet connection. The Microsoft Entra joined sign-in process doesn't use an on-premises domain controller for connectivity, and is faster than a traditional domain-based sign-in.

    Traditional domain joined PCs require connectivity to domain controllers for initial sign-in.
- **Deploy from anywhere**

    To deploy new devices, administrators can be anywhere with an internet connection. You can provision or reset devices, and have the devices ready quicker than traditional provisioning, possibly in minutes. The reliance on on-premises resources is reduced, which simplifies the endpoint requirements and endpoint management.
- **Simplified management for all platforms**

    Users and administrators get a unified management experience for all platforms, including Android, iOS/iPadOS, macOS, and Windows. With Intune, you can manage mobile and non-mobile devices and operating systems. You don't need to rely on complex group policy management.
- **Provide a secure Single-Sign-On (SSO) experience to cloud and on-premises apps**

    Cloud-native endpoints include native single sign-on (SSO) for cloud and [on-premises resources](/en-us/entra/identity/devices/device-sso-to-on-premises-resources), such as file servers, print servers, and web applications.
- **Secure access without passwords**

    With [Windows Hello for Business](/en-us/windows/security/identity-protection/hello-for-business/hello-overview), end users can sign in to their device, and access resources without passwords.

    For more specific information, go to [Password-less Strategy](/en-us/windows/security/identity-protection/hello-for-business/passwordless-strategy).
- **Seamless experience for documents, settings, and preferences**

    With [OneDrive](/en-us/onedrive/plan-onedrive-enterprise), end users automatically gain access to their documents, can restore any previous Office and Windows settings, and avoid spending time recovering data.

    For example, you can store the following user data on OneDrive:

    - Windows wallpaper
    - Automatic sync of documents and desktop files to OneDrive
    - Office settings
    - Outlook email signatures
    - Microsoft Edge settings

    When user data is stored on OneDrive, it can synchronize the data with all user endpoints.

## How to get started

The [High level planning guide to move to cloud-native endpoints](planning-guide) is a good resource. It covers the following areas:

- **Plan**: When ready to move to cloud-native endpoints, organizations focus on several key areas:

    - Review your existing workloads for modernization, and determine the next steps to support cloud-native.
    - Be prepared to change operational processes and procedures.
    - Get your end users ready for change.

    For more specific information, go to the [High level planning guide to move to cloud-native endpoints](planning-guide).
- **Create a Proof of Concept**: Do an initial proof of concept (POC). The goal is to understand changes and their impact.

    For more specific information, go to the [High level planning guide to move to cloud-native endpoints](planning-guide).

## Follow the cloud-native endpoints guidance

1. 🡺 **Overview: What are cloud-native endpoints?** (*You are here*)
2. [Tutorial: Set up cloud-native Windows endpoints with Microsoft Intune](tutorial-cloud-native-setup)
3. [Concept: Entra joined vs. Hybrid Entra joined](entra-join-types)
4. [Concept: Cloud-native endpoints and on-premises resources](on-premises-resources)
5. [High level planning guide](planning-guide)
6. [Known issues and important information](troubleshoot)