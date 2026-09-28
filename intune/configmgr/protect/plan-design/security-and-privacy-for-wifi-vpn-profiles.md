---
layout: Conceptual
title: Wi-Fi and VPN profile security and privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/security-and-privacy-for-wifi-vpn-profiles
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
description: Learn about the security recommendations for managing Wi-Fi and VPN profiles for devices in Configuration Manager.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 7933abaa-e79d-275c-818f-98c9491677f8
document_version_independent_id: ae99a1d8-3203-9dcb-4613-9422a5aff522
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/security-and-privacy-for-wifi-vpn-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md
cmProducts: []
platformId: cc6fe7dd-7e5f-71c4-753a-abdaca6a56f7
---

# Wi-Fi and VPN profile security and privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](resource-access-deprecation-faq).

## Security recommendations

Use the following security best practices when you manage Wi-Fi and VPN profiles for devices.

### Choose the most secure options that your Wi-Fi and VPN infrastructure and client operating systems can support

Wi-Fi and VPN profiles provide a convenient method to centrally distribute and manage Wi-Fi and VPN settings that your devices already support. Configuration Manager doesn't add Wi-Fi or VPN functionality. Identify, implement, and follow any security recommendations for your devices and infrastructure.

## Privacy information

You can use Wi-Fi and VPN profiles to configure client devices to connect to Wi-Fi and VPN servers. Then use Configuration Manager to evaluate whether those devices become compliant after the profiles are applied. The management point sends compliance information to the site server, and the information is stored in the site database. The information is encrypted when devices send it to the management point, but it isn't stored in encrypted format in the site database. The database retains the information until the site maintenance task **Delete Aged Configuration Management Data** deletes it. The default deletion interval is 90 days, but you can change it. Compliance information isn't sent to Microsoft.

By default, devices don't evaluate Wi-Fi and VPN profiles. In addition, you must configure the profiles, and then deploy them to users.

Before you configure Wi-Fi or VPN profiles, consider your privacy requirements.