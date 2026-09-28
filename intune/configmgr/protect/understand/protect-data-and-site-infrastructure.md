---
layout: Conceptual
title: Protect data and site infrastructure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/understand/protect-data-and-site-infrastructure
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
description: Learn how to protect your organization's resources from exposure or malicious attack with Configuration Manager.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 73389c48-9a87-bb34-59c8-36dc18816d21
document_version_independent_id: c273b9d7-3431-7e22-f695-6f0d15bfead9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/understand/protect-data-and-site-infrastructure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/understand/protect-data-and-site-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/understand/protect-data-and-site-infrastructure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
platformId: 0a764c29-ef75-0e31-05c6-6232640ec391
---

# Protect data and site infrastructure - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You want your users to securely access your organization's resources. Protect both your infrastructure and your data from exposure or malicious attack. Use Configuration Manager to enable access and help protect your organization's resources.

- [Endpoint Protection](../deploy-use/endpoint-protection) lets you manage the following Microsoft Defender policies for client computers:

    - Microsoft Defender Antimalware
    - Microsoft Defender Firewall
    - Microsoft Defender for Endpoint
    - Microsoft Defender Exploit Guard
    - Microsoft Defender Application Guard
    - Microsoft Defender Application Control

    Tip

    To manage endpoint protection on co-managed Windows 10 or later devices using the Microsoft Intune cloud service, switch the [**Endpoint Protection** workload](../../comanage/workloads#endpoint-protection) to Intune. For more information, see [Endpoint protection for Microsoft Intune](../../../device-configuration/endpoint-security/ref-endpoint-protection-settings-windows).
- Protect data stored on on-premises Windows clients with BitLocker Drive Encryption (BDE). Configuration Manager provides full BitLocker lifecycle management that can replace the use of Microsoft BitLocker Administration and Monitoring (MBAM). For more information, see [Plan for BitLocker management](../plan-design/bitlocker-management).

Use other components of Microsoft Intune to protect your devices. For more information, see [Protect devices with Microsoft Intune](../../../device-security/overview).