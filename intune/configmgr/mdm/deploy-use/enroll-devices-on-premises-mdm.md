---
layout: Conceptual
title: Enroll devices for on-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/enroll-devices-on-premises-mdm
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
description: Learn about methods to enroll devices for on-premises mobile device management (MDM) in Configuration Manager.
ms.date: 2020-01-13T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 7cebcac0-b5fd-96a7-8332-5279befeb374
document_version_independent_id: c44161ef-1348-0051-b38c-61e3258c0ec1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/enroll-devices-on-premises-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/enroll-devices-on-premises-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/enroll-devices-on-premises-mdm.md
cmProducts: []
platformId: 64ff462f-c775-913c-315b-44d21bf251f2
---

# Enroll devices for on-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To manage devices with Configuration Manager on-premises mobile device management (MDM), you first need to enroll them. Then Configuration Manager can communicate with the devices for management tasks. Configuration Manager provides two methods to enroll devices:

- **User enrollment**: Users start the enrollment process on their device. For user enrollment to succeed, install the trusted root certificate on the device, and provision the user for enrollment in client settings. To enroll a device, the user only needs to enter their credentials.

    For more information, see [How users enroll devices](user-enroll-devices-on-premises-mdm).
- **Bulk enrollment**: The user of the device doesn't start enrollment. You create a bulk enrollment package in Configuration Manager. When you open it on the device, the package provides the information required to enroll the device.

    For more information, see [How to bulk-enroll devices](bulk-enroll-devices-on-premises-mdm).

For more information on the OS versions that Configuration Manager supports for device enrollment in on-premises MDM, see [Supported configurations](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS).