---
layout: Conceptual
title: VPN profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/vpn-profiles
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
description: Learn how to use VPN profiles in Configuration Manager to deploy VPN settings to users in your organization.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 19312443-ed1f-d422-6b9e-4aac2369b63e
document_version_independent_id: 96b77452-ada4-a593-97e8-7611c3deab3c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/vpn-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/vpn-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/vpn-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 16d16286-f670-6a53-778e-eaa26f4e135f
---

# VPN profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

To deploy VPN settings to users in your organization, use VPN profiles in Configuration Manager. By deploying these settings, you minimize the end-user effort required to connect to resources on the company network.

For example, you want to configure all Windows 10 devices with the settings required to connect to a file share on the internal network. Create a VPN profile with the settings necessary to connect to the internal network. Then deploy this profile to all users that have devices running Windows 10. These users see the VPN connection in the list of available networks and can connect with little effort.

When you create a VPN profile, you can include a wide range of security settings. These settings include certificates for server validation and client authentication that you provision with Configuration Manager certificate profiles. For more information, see [Certificate profiles](introduction-to-certificate-profiles).

Note

Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](../../core/servers/manage/optional-features).

## Supported platforms

The following table describes the VPN profiles you can configure for various device platforms.

| Connection type | Windows 8.1 | Windows RT | Windows RT 8.1 | Windows 10 |
| --- | --- | --- | --- | --- |
| **Pulse Secure** | Yes | No | Yes | Yes |
| **F5 Edge Client** | Yes | No | Yes | Yes |
| **Dell SonicWALL Mobile Connect** | Yes | No | Yes | Yes |
| **Check Point Mobile VPN** | Yes | No | Yes | Yes |
| **Microsoft SSL (SSTP)** | Yes | Yes | Yes | No |
| **Microsoft Automatic** | Yes | Yes | Yes | No |
| **IKEv2** | Yes | Yes | Yes | No |
| **PPTP** | Yes | Yes | Yes | No |
| **L2TP** | Yes | Yes | Yes | No |