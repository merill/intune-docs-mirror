---
layout: Conceptual
title: Deploy Endpoint Privilege Management with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/epm/deploy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: mikedano
ms.subservice: suite
description: Understand the steps and phases for deploying Endpoint Privilege Management with Microsoft Intune.
ms.date: 2025-09-10T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a84a535d-a326-2ade-c276-d60dda6b1e05
document_version_independent_id: a84a535d-a326-2ade-c276-d60dda6b1e05
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/epm/deploy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: epm/deploy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/epm/deploy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 353c46db-a76e-84fa-2257-40e1dff20431
---

# Deploy Endpoint Privilege Management with Microsoft Intune - Microsoft Intune | Microsoft Learn

To deploy Endpoint Privilege Management (EPM), start by enabling reporting, then use reports to create rules for elevation. This article describes some common deployment scenarios and outlines the recommended deployment phases for your organization.

- [Windows elevation settings policy](manage-elevation-settings).
- [Windows elevation rules policy](create-elevation-rules).
- [Reusable settings groups](create-elevation-rules#reusable-settings-groups), which are optional configurations for your elevation rules.

## Deployment overview

EPM can help control the elevation of applications in Intune and [Local Users and Groups](../device-configuration/endpoint-security/account-protection) can be used to control the local administrators group and transition users from administrators to standard users.

The common deployment phases are:

![The five phases to deploy EPM.](media/deploy/epm-deploy-phases.png)

- **Phase 1: Auditing** - Enable EPM client and enable reporting collection using an [elevation settings policy](manage-elevation-settings).
- **Phase 2: Persona identification** - Identity groups of users with common requirements.
- **Phase 3: Build rules** - Use [EPM reports](monitor-reports) to create [elevation rules](create-elevation-rules) for different personas.
- **Phase 4: Monitoring** - Iterate and refine rules, identify new scenarios.
- **Phase 5: Review user privileges** - Identify and optionally move users from administrator to standard user using [Local Users and Groups](../device-configuration/endpoint-security/account-protection#manage-local-groups-on-windows-devices). Consider enabling [support approved elevation](manage-support-approvals) so that users can request elevation for apps that aren't covered by rules.

Repeat phases 2 to 5 continuously to ensure your users have least privilege in line with [Zero Trust principles](../fundamentals/zero-trust).

The common deployment scenarios for EPM are:

| Scenario | Local User (Before) | Local User (After) | Example Role | Use Case |
| --- | --- | --- | --- | --- |
| 1 | Admin | Admin | IT Support Technicians | A certain subset of users required ongoing local admin – but you want to gain security improvements by using EPM. |
| 2 | Admin | Standard User | Information Workers | You want to move users with local admin rights to standard users, with minimal disruption. You want to allow them to request an app to run as admin on occasion. For step by step instructions on how to achieve this scenario with EPM, see [Using EPM to transition users from administrator to standard users](tutorial-admin-to-standard-user) |
| 2 | Standard User | Standard User | Developers | You want to allow specific users to 'elevate up' without granting local admin rights or using [LAPS](../device-security/laps/overview). |