---
layout: Conceptual
title: Integrate an MDM provider with Windows Autopilot device association | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/device-association/mdm-provider-integration
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Learn how a mobile device management provider can request limited access to integrate its service with Windows Autopilot device association.
ms.date: 2026-10-16T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 21f85f33-86f2-39b4-1935-f7ad3105c4e9
document_version_independent_id: 21f85f33-86f2-39b4-1935-f7ad3105c4e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/device-association/mdm-provider-integration.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/device-association/mdm-provider-integration
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/device-association/mdm-provider-integration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: af63f6c6-ea7b-317f-cb49-09cb8f22e66e
---

# Integrate an MDM provider with Windows Autopilot device association | Microsoft Learn

Windows Autopilot device association can support integration with a mobile device management (MDM) provider other than Microsoft Intune. Provider integration is available through a limited-access onboarding process. Microsoft must authorize the Microsoft Entra application that the provider uses before the application can access the device association service.

Important

This process is for MDM providers that are building device association into their service. It doesn't provide an individual customer or administrator with direct access to the device association service.

## Prerequisites

Before requesting access, the MDM provider should:

- Support Windows device enrollment and management by using the Windows MDM protocols. For more information, see [Mobile Device Management overview](/en-us/windows/client-management/mdm-overview).
- Integrate its MDM service with Microsoft Entra ID. For more information, see [Microsoft Entra integration with MDM](/en-us/windows/client-management/azure-active-directory-integration-with-mdm).
- Register the Microsoft Entra application that the service uses to call device association APIs.
- Define how customers authorize the provider to perform device association operations for their tenant.

## Request access

Contact your Microsoft representative to request onboarding for Windows Autopilot device association. Include the following information:

- The provider's legal company name and MDM product name.
- Primary business and technical contacts.
- The Microsoft Entra tenant ID for the provider.
- The application (client) ID for each Microsoft Entra application and environment that requires access.
- A description of the device association scenarios that the integration supports.
- The expected customer scale, geographic availability, and planned release timeline.

Microsoft reviews the provider identity, application identity, and proposed use case. Microsoft might request additional technical, security, privacy, or compliance information during the review.

Note

Submitting a request doesn't guarantee approval. Microsoft doesn't publish a fixed review timeline for limited-access onboarding.

## Complete technical onboarding

If the request is approved, Microsoft:

1. Authorizes the approved Microsoft Entra application identity to use the device association service.
2. Provides the provider with the applicable API, permission, and validation requirements.
3. Defines the testing and production-readiness steps that must be completed before the integration is made available to customers.

Access is associated with the approved application identity and use case. It isn't transferable to another application or product. Contact Microsoft before changing an approved application ID, adding an environment, or materially changing the integration scenario.

## Provider responsibilities

An approved MDM provider is responsible for:

- Using device association access only for the approved MDM integration and scenarios.
- Ensuring that each customer authorizes the provider to perform device association operations for the customer's tenant.
- Requesting only the permissions required for the integration.
- Protecting credentials and device, tenant, and association data.
- Maintaining audit records for device association operations.
- Providing customer support for the provider's implementation.
- Notifying Microsoft about security incidents, ownership changes, or changes to the approved application identity or use case.