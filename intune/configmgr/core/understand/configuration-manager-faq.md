---
layout: FAQ
title: Microsoft Configuration Manager FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/configuration-manager-faq
summary: >
  <p><em>Applies to: Configuration Manager (current branch, technical preview branch)</em></p>

  <p>Configuration Manager is part of the Microsoft Intune family of products. This article provides answers to frequently asked questions.</p>
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
description: Frequently asked questions about Microsoft Configuration Manager
ms.date: 2021-04-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: faq
ms.collection: highpri
locale: en-us
document_id: 674d2576-d2d5-b6ba-23de-5f2e431f9976
document_version_independent_id: 674d2576-d2d5-b6ba-23de-5f2e431f9976
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/configuration-manager-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/configuration-manager-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/configuration-manager-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 768319ab-4459-edf7-f838-51d4ac82fd62
---

# Microsoft Configuration Manager FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch, technical preview branch)*

Configuration Manager is part of the Microsoft Intune family of products. This article provides answers to frequently asked questions.

## What is the Microsoft Intune family of products?

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune with simplified licensing. Continue to use your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

The following Microsoft management solutions are all now part of the **Microsoft Intune** brand:

- [Configuration Manager](../../)
- [Intune](../../../intune-service/)
- [Endpoint analytics](../../../endpoint-analytics/)
- [Windows Autopilot](/en-us/autopilot/enrollment-autopilot/)

## What things change in Configuration Manager and the Microsoft Intune family of products?

Aside from the name change, Configuration Manager still functions the same.

Most notably, the Start menu folder names changed for common components, such as the [Configuration Manager console](../servers/manage/admin-console#bkmk_open) and [Software Center](software-center#bkmk_open).

## How do we refer to the product now?

- When referring to the entire solution that includes all components: **Microsoft Intune family of products**
- When referring to the on-premises component:

    - On first reference, use the full brand name: **Microsoft Configuration Manager**
    - For general use: **Configuration Manager**
    - For space-constrained use: **ConfigMgr**, only in instances where the general use name doesn't fit

## Are there any licensing changes?

If you're licensed for Configuration Manager, then you're also licensed for Intune to [co-manage](../../comanage/overview) your Windows PCs. For more information, see the [Product and licensing FAQ](product-and-licensing-faq#what-changes-with-licensing-for-co-management-in-the-microsoft-intune-family-of-products-).

## Why do I still see "System Center Configuration Manager" some places?

It takes time to make changes across all products, services, and supporting materials like documentation.

There are also some fundamental components that may never change. The main Windows service on site servers is still **SMS\_Executive**.