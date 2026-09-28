---
layout: Conceptual
title: Use the Intune Data Warehouse - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/create-reports
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.reviewer: jamiesil
ms.subservice: developer
description: Use the Intune Data Warehouse to build reports that provide insight into your enterprise mobile environment.
ms.date: 2026-03-31T00:00:00.0000000Z
ms.topic: reference
ai-usage: ai-assisted
locale: en-us
document_id: 77d49d4f-6fe6-2107-cee1-36101c432cfe
document_version_independent_id: 77d49d4f-6fe6-2107-cee1-36101c432cfe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/create-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/create-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/create-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 993db920-81ca-2c92-8caa-ed91932eb7d3
---

# Use the Intune Data Warehouse - Microsoft Intune | Microsoft Learn

Important

The Intune Data Warehouse (beta) connector in Power BI (connector v1) is being retired. If your Power BI reports use connector v1, migrate to the Intune connector v2 or OData Feed connector. For migration steps, see [Connect to the Data Warehouse with Power BI](connect-power-bi#migrate-from-connector-v1).

Use the Intune Data Warehouse to build reports that provide insight into your enterprise mobile environment. For example, some of the reports include:

- Trend of users enrolling in Intune so you can optimize your license purchases
- App and OS versions breakdown so you can review that status of mobile devices
- Enrollment and device compliance trends so you can smoothly roll out policy updates

## Data Warehouse benefits

The Data Warehouse provides you access to more information about your mobile environment than the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). With the Intune Data Warehouse you can access:

- Historical Intune data
- Data refreshed on a daily cadence
- A data model using the OData standard

Note

If you are a using co-managed mobile device management (MDM) with Microsoft Configuration Manager and Microsoft Intune, you need to retrieve your data from Configuration Manager. The Intune Data Warehouse only contains Intune data. You can use a Configuration Manager Power BI dashboard for your custom reports. For related information, see [Power BI Desktop](/en-us/configmgr/develop/adminservice/usage#power-bi-desktop).

Important

You can now use the v1.0 version of the Intune Data Warehouse by setting the query parameter `api-version=v1.0`. Updates to collections in the Data Warehouse are additive in nature and do not break existing scenarios. You can try out the latest functionality of the Data Warehouse by using the beta version. To use the beta version, your URL must contain the query parameter `api-version=beta`. The beta version offers features before they are made generally available as a supported service. As Intune adds new features, the beta version may change behavior and data contracts. Any custom code or reporting tools dependent on the beta version may break with ongoing updates.