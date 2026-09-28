---
layout: Conceptual
title: Hardware inventory security privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-hardware-inventory
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
description: Get security and privacy information for hardware inventory in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 98c5f60a-dd2d-c58e-eead-8187cb85b53f
document_version_independent_id: 0552f1e1-abb0-b322-1957-6a26003901ed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-hardware-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/security-and-privacy-for-hardware-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-hardware-inventory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: adaf9251-9476-e188-360a-d5b0d43d8ed7
---

# Hardware inventory security privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic contains security and privacy information for hardware inventory in Configuration Manager.

## Security best practices for hardware inventory

Use the following security best practices for when you collect hardware inventory data from clients:

| Security best practice | More information |
| --- | --- |
| Sign and encrypt inventory data | When clients communicate with management points by using HTTPS, all data that they send is encrypted by using SSL. However, when client computers use HTTP to communicate with management points on the intranet, client inventory data and collected files can be sent unsigned and unencrypted. Make sure that the site is configured to require signing and use encryption. In addition, if clients can support the SHA-256 algorithm, select the option to require SHA-256. |
| Do not collect IDMIF and NOIDMIF files in high-security environments | You can use IDMIF and NOIDMIF file collection to extend hardware inventory collection. When necessary, Configuration Manager creates new tables or modifies existing tables in the Configuration Manager database to accommodate the properties in IDMIF and NOIDMIF files. However, Configuration Manager does not validate IDMIF and NOIDMIF files, so these files could be used to alter tables that you do not want altered. Valid data could be overwritten by invalid data. In addition, large amounts of data could be added and the processing of this data might cause delays in all Configuration Manager functions. To mitigate these risks, configure the hardware inventory client setting **Collect MIF files** as **None**. |

### Security issues for hardware inventory

Collecting inventory exposes potential vulnerabilities. Attackers can perform the following:

- Send invalid data, which will be accepted by the management point even when the software inventory client setting is disabled and file collection is not enabled.
- Send excessively large amounts of data in a single file and in lots of files, which might cause a denial of service.
- Access inventory information as it is transferred to Configuration Manager.

    Because a user with local administrative privileges can send any information as inventory data, do not consider inventory data that is collected by Configuration Manager to be authoritative.

    Hardware inventory is enabled by default as a client setting.

## Privacy information for hardware inventory

Hardware inventory allows you to retrieve any information that is stored in the registry and in WMI on Configuration Manager clients. Software inventory allows you to discover all files of a specified type or to collect any specified files from clients. Asset Intelligence enhances the inventory capabilities by extending hardware and software inventory and adding new license management functionality.

Hardware inventory is enabled by default as a client setting and the WMI information collected is determined by options that you select. Software inventory is enabled by default but files are not collected by default. Asset Intelligence data collection is automatically enabled, although you can select the hardware inventory reporting classes to enable.

Inventory information is not sent to Microsoft. Inventory information is stored in the Configuration Manager database. When clients use HTTPS to connect to management points, the inventory data that they send to the site is encrypted during the transfer. If clients use HTTP to connect to management points, you have the option to enable inventory encryption. The inventory data is not stored in encrypted format in the database. Information is retained in the database until it is deleted by the site maintenance tasks **Delete Aged Inventory History** or **Delete Aged Collected Files** every 90 days. You can configure the deletion interval.

Before you configure hardware inventory, software inventory, file collection, or Asset Intelligence data collection, consider your privacy requirements.