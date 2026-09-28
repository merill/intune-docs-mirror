---
layout: Conceptual
title: Wi-Fi and VPN profile prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/prerequisites-for-wifi-vpn-profiles
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
description: Learn about the prerequisites to manage Wi-Fi profiles and VPN profiles in Configuration Manager
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 5c0475d6-045f-56de-0f58-c110ab944478
document_version_independent_id: 67ac7109-7e18-2cd5-2882-1576691b3180
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/prerequisites-for-wifi-vpn-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/prerequisites-for-wifi-vpn-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/prerequisites-for-wifi-vpn-profiles.md
cmProducts: []
platformId: aed1e92c-d2b2-2a90-5869-2abd9c3353a6
---

# Wi-Fi and VPN profile prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](resource-access-deprecation-faq).

Wi-Fi and VPN profiles in Configuration Manager have dependencies only within the product.

You need the following security permissions to manage company resource access settings, such as certificate profiles, Wi-Fi profiles, and VPN profiles:

- To view and manage alerts and reports for Wi-Fi and profiles: **Create**, **Delete**, **Modify**, **Modify Report**, **Read**, and **Run Report** for the **Alerts** object.
- To create and manage certificate profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Certificate Profile** object.
- To manage Wi-Fi, certificate, and VPN profile deployments: **Deploy Configuration Policies**, **Modify Client Status Alert**, **Read**, and **Read Resource** for the **Collection** object.
- To manage all configuration policies: **Create**, **Delete**, **Modify**, **Read**, and **Set Security Scope** for the **Configuration Policy** object.
- To run queries that are related to Wi-Fi and VPN profiles: **Read** permission for the **Query** object.
- To view Wi-Fi and VPN profiles information in the Configuration Manager console: **Read** permission for the **Site** object.
- To view status messages for Wi-Fi and VPN profiles: **Read** permission for the **Status Messages** object.
- To create and modify the Trusted CA certificate profile: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Trusted CA Certificate Profile** object.
- To create and manage VPN profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **VPN Profile** object.
- To create and manage Wi-Fi profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Wi-Fi Profile** object.

The **Company Resource Access Manager** built-in security role includes these permissions that are required to manage Wi-Fi profiles in Configuration Manager. For more information, see [Configure security](../../core/plan-design/security/configure-security).