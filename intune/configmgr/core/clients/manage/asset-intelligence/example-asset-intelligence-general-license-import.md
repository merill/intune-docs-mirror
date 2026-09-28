---
layout: Conceptual
title: Example Asset Intelligence general license import file - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import
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
description: Use a sample Asset Intelligence general license file to help import software licenses in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: d5ab13fe-f225-da61-d3f1-e644b3cb436a
document_version_independent_id: 33c66189-1ba9-5918-cf09-462451d42687
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60932d05-feee-4685-a73b-595e25dd9318
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c43bb58b-1190-419b-8d18-e6052371b599
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: c6865740-dd3c-2d59-9900-28193ec3d685
---

# Example Asset Intelligence general license import file - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The example information in this topic can be used to create a sample general software license file to import software licenses into the Asset Intelligence catalog by using the Import Software License Wizard. You can copy and paste the following table into a new Microsoft Excel spreadsheet and save it with a .csv file name extension to be used as an example general software license import file for testing purposes. When creating the license import file, all header fields are required while only Name, Publisher, Version, and EffectiveQuantity data values are required in the spreadsheet. For more information about importing software licenses to the Asset Intelligence catalog, see [Configuring Asset Intelligence](configuring-asset-intelligence).

| Name | Publisher | Version | Language | EffectiveQuantity | PONumber | ResellerName | DateOfPurchase | SupportPurchased | SupportExpirationDate | Comments |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Software Title 1 | Software publisher | 1.01 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 2 | Software publisher | 1.02 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 3 | Software publisher | 1.03 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 4 | Software publisher | 1.04 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 5 | Software publisher | 1.05 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 6 | Software publisher | 1.06 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 7 | Software publisher | 1.07 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 8 | Software publisher | 1.08 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 9 | Software publisher | 1.09 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |
| Software title 10 | Software publisher | 1.10 | English | 1 | Purchase number | Reseller name | 10/10/2010 | 0 | 10/10/2012 | Comment |