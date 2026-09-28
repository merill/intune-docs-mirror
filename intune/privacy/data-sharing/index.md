---
layout: Conceptual
title: Data security and sharing in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- privacy
- essentials-privacy
- sub-data-privacy
description: Learn how personal data is secured and shared in Intune.
ms.date: 2023-12-07T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: angerobe
locale: en-us
document_id: be3eabc7-f4ae-5416-1e25-b0c2f00da739
document_version_independent_id: be3eabc7-f4ae-5416-1e25-b0c2f00da739
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/data-sharing/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/data-sharing/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/data-sharing/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cf8f81d-2989-4e5d-aa91-5191d10a3323
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/1cb9c90f-9a3f-4389-8367-0a20c542621f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 63de067d-7ab0-69ba-57bf-fa799d97fb4d
---

# Data security and sharing in Intune - Microsoft Intune | Microsoft Learn

## Data security

Microsoft Intune is a key component of the Microsoft Enterprise Mobility and Security Suite cloud service offering. To support the [data governance strategy](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), all Microsoft cloud services are developed with [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) and [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/) methodologies.

Microsoft Intune follows the same technical and organizational measures that the Microsoft Azure service teams take for securing against data breach processes.

For more information, see the [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

### Data breach reporting

When a Customer-Reportable Security Incident (CRSI) is identified, customers are notified. This process includes working with the Microsoft 365 team to communicate breach notification for any Microsoft 365 customers using Intune.

## Data sharing

When tenant admins turn on certain functionality (like the Apple Device Enrollment Program), Microsoft Intune obtains admin consent for sharing data with the appropriate third parties. In such cases, Intune may share personal data with:

- Third parties acting as Microsoft's agents.
- Third parties not acting as Microsoft's agents, but only when tenant admins explicitly grant Intune permission to do so.

All third parties acting as Microsoft agents are included in the [Online Services Subcontractor list](https://aka.ms/Online_Serv_Subcontractor_List).

Sharing data with such entities is done to aid customer and technical support, service maintenance, and other operations.

A tenant's contract with the third party governs the Intune personal data held in the third party's service. It also grants Intune the permission to transmit data to the third party service.

For information about data shared with certain third parties, see the following articles:

- [Data Intune sends to Apple](ref-intune-to-apple)
- [Data Intune sends to Google](ref-intune-to-google)
- [Data Apple sends to Intune](ref-apple-to-intune)
- [Data Google sends to Intune](ref-google-to-intune)
- [Data Jamf Pro sends to Intune](ref-jamf-to-intune)

### Microsoft Configuration Manager data sharing

Microsoft Intune doesn't share any data with Configuration Manager. Configuration Manager is an on-premise product deployed, managed, and operated directly by the customer. The diagnostics and usage data that is collected by Configuration Manager are only to improve the installation experience, quality, and security of future releases.

To learn more, see [Diagnostics and usage data for Configuration Manager](/en-us/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data).