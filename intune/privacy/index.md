---
layout: Conceptual
title: Privacy and personal data in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Learn what personal data is collected and processed in Intune.
ms.date: 2025-04-07T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: intuneprivacy
ms.collection:
- M365-identity-device-management
- privacy
- essentials-privacy
- sub-data-privacy
locale: en-us
document_id: 0e9c5e78-e377-e074-b4a6-b4354e7a45fe
document_version_independent_id: 0e9c5e78-e377-e074-b4a6-b4354e7a45fe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 9be02726-6444-e0a4-8119-b338239f6fbd
---

# Privacy and personal data in Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune operates as a data processor on behalf of the customer as necessary to provide customers with the requested service as set forth in the [Microsoft Online Services Terms (OST)](https://go.microsoft.com/fwlink/p/?LinkId=2098215). Personal data is provided directly through Customer Administrator use of Intune through the Azure portal or Microsoft Intune admin center, or from customer devices when enrolled for management. Personal data is also collected at third-party services per the customer's instructions such as [setting up Apple Volume Purchasing Program](data-sharing/#data-sharing). Customers can receive, transmit, and store data on devices managed by Intune. Personal data is processed and stored within the audited compliance boundary of the Intune service under the technical security measures assured through [Microsoft Online Services Terms (OST)](https://go.microsoft.com/fwlink/p/?LinkId=2098215).

To help Intune admins understand how your data's privacy is protected, this article explains how Intune collects, stores, retains, processes, secures, shares, audits, and exports personal data. It also covers how to review, correct, and delete your personal data.

Microsoft Intune doesn't use any personal data collected as part of providing the service for profiling, advertising, or marketing purposes.

Note

If you're interested in viewing or deleting personal data, see the [Azure Data Subject Requests for the GDPR](/en-us/microsoft-365/compliance/gdpr-dsr-azure) article. If you're looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## Compliance certifications

Intune is covered under several compliance certifications, and regulatory standards. The following table provides a sample of the key certifications that are covered:

| Certification or Standard | Description | Applicability |
| --- | --- | --- |
| [GDPR](/en-us/compliance/regulatory/gdpr) | EU General Data Protection Regulation for data privacy | European Union |
| [ISO 27001](/en-us/compliance/regulatory/offering-iso-27001) | International standard for information security management | Global |
| [HIPAA](/en-us/compliance/regulatory/offering-hipaa-hitech) | U.S. Health Insurance Portability and Accountability Act | United States |
| [SOC 2 Type 2](/en-us/compliance/regulatory/offering-soc-2) | Service Organization Controls for data security | Global |

Note

Microsoft Intune helps your organization meet regulatory compliance standards. Intune supports additional certifications, such as [ISO 22301](/en-us/compliance/regulatory/offering-iso-22301), [ISO/IEC 27017](/en-us/compliance/regulatory/offering-iso-27017), [ISO/IEC 27018](/en-us/compliance/regulatory/offering-iso-27018), [ISO/IEC 27701](/en-us/compliance/regulatory/offering-iso-27701), [SOC 1 Type 2](/en-us/compliance/regulatory/offering-soc-1), [SOC 3](/en-us/compliance/regulatory/offering-soc-3), and [WCAG](/en-us/compliance/regulatory/offering-wcag-2-1).

For a complete list, see [Microsoft compliance offerings](/en-us/compliance/regulatory/offering-home).

## Your company terms and conditions

In addition to the [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement), you can [include privacy statements in your company's terms and conditions for end users](../app-management/configuration/configure-company-portal). Such privacy statements can include information about the usage and privacy of the end user's personal data.

You can display your company's terms and conditions in the Intune Company Portal app. This way, users can review the terms and conditions, including the privacy statement, before they enroll in Intune and access company assets and data.