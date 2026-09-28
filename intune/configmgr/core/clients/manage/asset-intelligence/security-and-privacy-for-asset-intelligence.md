---
layout: Conceptual
title: Asset Intelligence security & privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence
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
description: Security guidance and privacy information for Asset Intelligence in Configuration Manager.
ms.date: 2021-05-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 27e2228a-fb7e-66c6-b49e-5114efc8f7d6
document_version_independent_id: b9026a54-b837-8265-5ca8-71fa8ce79fe1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: e4d039df-139e-c625-cf05-7d085c021907
---

# Asset Intelligence security & privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article contains security guidance and privacy information for Asset Intelligence in Configuration Manager.

## Security guidance

### Secure license files

When you import a Microsoft Volume Licensing file or a General License Statement file, secure the file and communication channel. Configure NTFS permissions to make sure that only authorized users can access the license files. Use Server Message Block (SMB) signing to keep the integrity of the data when it's transferred to the site server during the import process.

### Limit permissions for users who import license files

Use the principle of least permissions to import the license files. Use [role-based administration](../../../understand/fundamentals-of-role-based-administration) to grant the **Manage Asset Intelligence** permission to the administrative user who imports license files. The built-in role of **Asset Manager** includes this permission.

## Privacy information

Asset Intelligence extends the inventory capabilities of Configuration Manager to provide a higher level of asset visibility. Asset Intelligence information collection isn't automatically enabled. You can modify the type of information collected by enabling hardware inventory reporting classes. For more information, see [Configure Asset Intelligence](configuring-asset-intelligence).

Configuration Manager stores Asset Intelligence information in the site database the same as inventory information. When clients connect to management points by using HTTPS, the data is always encrypted during transfer to the management point. When clients connect by using HTTP, configure the inventory data transfer to be [signed and encrypted](../../../plan-design/security/configure-security#signing-and-encryption). Inventory data isn't stored in an encrypted format in the database. Information is kept in the database until the site maintenance task [Delete Aged Inventory History](../../../servers/manage/reference-for-maintenance-tasks#delete-aged-inventory-history) deletes it every 90 days by default. You can configure the deletion interval.

Asset Intelligence doesn't send information about users, computers, or license usage to Microsoft. You can choose to send System Center Online requests for categorization. For these requests, you tag one or more uncategorized software titles and send them to Microsoft for research and categorization. After you upload a software title, Microsoft researchers identify and categorize the software. They then make that information available to all customers who use the online service.

When you submit information to System Center Online, understand the following privacy implications:

- Upload applies only to generic software title information that you choose to send to Microsoft. For example, software name and publisher. Inventory information isn't sent to Microsoft.
- Upload never occurs automatically, and the system isn't designed for this task to be automated. Manually select and approve the upload of each software title.
- Before the upload process starts, the Configuration Manager console shows you exactly what data it will upload.
- License information isn't sent to Microsoft. Configuration Manager stores the license information in a separate area of the site database, and it can't be sent to Microsoft.
- Any software title that you upload becomes public. The knowledge of that software and its categorization become part of the online Asset Intelligence catalog. Other customers can then download the catalog updates.
- The source of the software title isn't recorded in the Asset Intelligence catalog, and it isn't made available to other customers. Still verify that you don't include any application titles that contain any private information.
- You can't recall uploaded data.