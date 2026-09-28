---
layout: Conceptual
title: Plan on-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/plan-design/plan-on-premises-mdm
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Plan for on-premises mobile device management to manage mobile devices in Configuration Manager
ms.date: 2020-01-09T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 947c7037-6d4f-2676-3215-0cfb3612c72e
document_version_independent_id: ca70eaad-4909-ea1f-520a-f1068e981dc1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/plan-design/plan-on-premises-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/plan-design/plan-on-premises-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/plan-design/plan-on-premises-mdm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: 2679e7ef-bbe6-99c9-9e60-62e02c59aa10
---

# Plan on-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

There are several key areas to review when you're planning to implement on-premises mobile device management (MDM) in Configuration Manager:

- Supported devices and OS versions
- Required site system roles
- Secure communication
- Device enrollment

Important

While the site or any mobile device doesn't connect to Microsoft Intune, your organization still requires Intune licenses to use this feature. For more information, see [Microsoft Intune licensing](/en-us/mem/fundamentals/licensing).

Consider the following requirements before preparing the Configuration Manager infrastructure to handle on-premises MDM.

## Supported devices

The current branch of Configuration Manager supports enrollment in on-premises mobile device management for devices running Windows 10. These device types primarily include laptops, IoT, and Surface Hub. For more information and the list of specific editions, see [Supported OS versions for clients and devices](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS).

## Site system roles

On-premises MDM requires at least one of the following site system roles:

- **Enrollment proxy point** to support enrollment requests.
- **Enrollment point** to support device enrollment.
- **Device management point** for policy delivery. This role is a variation of the management point, but allows for mobile device management.
- **Distribution point** for content delivery.

Depending on the needs of your organization, you can install these roles on the single server or separately on different servers.

Note

You need to configure each role used for on-premises MDM as an HTTPS endpoint for communicating with trusted devices. For more information, see Required trusted communications.

For more general information, see [Plan for site system servers and roles](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles).

## Trusted communications

On-premises MDM requires that you enable site system roles for HTTPS communications. Depending on your needs, you can use your organization's certificate authority (CA) to establish the trusted connections between servers and devices. You can also use a publicly available CA to be the trusted authority. Either way, you need to configure the following certificates:

- A **web server certificate** in IIS on the servers hosting the required site system roles. If one server hosts multiple site system roles, then you only need one certificate for that server. If each role is on a separate server, each server needs a separate certificate.
- The **trusted root certificate** of the CA that issues the web server certificates. Install this root certificate on all devices that need to connect to the site system roles.

For more information, see [Set up certificates for trusted communications in on-premises MDM](../get-started/set-up-certificates-on-premises-mdm).

## Device enrollment

To enable device enrollment for on-premises MDM:

- Grant users permission to enroll via client settings
- Configure devices for trusted communications with the site system servers hosting the required roles

As an alternative to user-initiated enrollment, you can set up a bulk enrollment package. This package allows the device to enroll without user intervention. Deliver the package to the device before it's provisioned for use or after it goes through its OOBE process.

For more information, see [Set up device enrollment for on-premises MDM](../get-started/set-up-device-enrollment-on-premises-mdm).