---
layout: Conceptual
title: Software inventory security privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-software-inventory
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
description: Get security and privacy information for software inventory in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 42941385-4aaa-f108-31bc-29fde00e17f0
document_version_independent_id: 3eb2fcfa-bc18-0924-3de2-3f35dfe4b5a2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-software-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/security-and-privacy-for-software-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/security-and-privacy-for-software-inventory.md
cmProducts: []
platformId: ba90dbd2-cab4-3bd6-fd19-6a3500ee853f
---

# Software inventory security privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic contains security and privacy information for software inventory in Configuration Manager.

## Security best practices for software inventory

Use the following security best practices for when you collect software inventory data from clients:

| Security best practice | More information |
| --- | --- |
| Sign and encrypt inventory data | When clients communicate with management points by using HTTPS, all data that they send is encrypted by using SSL. However, when client computers use HTTP to communicate with management points on the intranet, client inventory data and collected files can be sent unsigned and unencrypted. Make sure that the site is configured to require signing and use encryption. In addition, if clients can support the SHA-256 algorithm, select the option to require SHA-256. |
| Do not use file collection to collect critical files or sensitive information | Configuration Manager software inventory uses all the rights of the LocalSystem account, which has the ability to collect copies of critical system files, such as the registry or security account database. When these files are available at the site server, someone with the Read Resource rights or NTFS rights to the stored file location could analyze their contents and possibly discern important details about the client in order to be able to compromise its security. |
| Restrict local administrative rights on client computers | A user with local administrative rights can send invalid data as inventory information. |

### Security issues for software inventory

Collecting inventory exposes potential vulnerabilities. Attackers can perform the following:

- Send invalid data, which will be accepted by the management point even when the software inventory client setting is disabled and file collection is not enabled.
- Send excessively large amounts of data in a single file and in lots of files, which might cause a denial of service.
- Access inventory information as it is transferred to Configuration Manager.

    If users know that they can create a hidden file named **Skpswi.dat** and place it in the root of a client hard drive to exclude it from software inventory, you will not be able to collect software inventory data from that computer.

    Because a user with local administrative privileges can send any information as inventory data, do not consider inventory data that is collected by Configuration Manager to be authoritative.

    Software inventory is enabled by default as a client setting.

## Privacy information for software inventory

Hardware inventory allows you to retrieve any information that is stored in the registry and in WMI on Configuration Manager clients. Software inventory allows you to discover all files of a specified type or to collect any specified files from clients. Asset Intelligence enhances the inventory capabilities by extending hardware and software inventory and adding new license management functionality.

Hardware inventory is enabled by default as a client setting and the WMI information collected is determined by options that you select. Software inventory is enabled by default but files are not collected by default. Asset Intelligence data collection is automatically enabled, although you can select the hardware inventory reporting classes to enable.

Inventory information is not sent to Microsoft. Inventory information is stored in the Configuration Manager database. When clients use HTTPS to connect to management points, the inventory data that they send to the site is encrypted during the transfer. If clients use HTTP to connect to management points, you have the option to enable inventory encryption. The inventory data is not stored in encrypted format in the database. Information is retained in the database until it is deleted by the site maintenance tasks **Delete Aged Inventory History** or **Delete Aged Collected Files** every 90 days. You can configure the deletion interval.

Before you configure hardware inventory, software inventory, file collection, or Asset Intelligence data collection, consider your privacy requirements.