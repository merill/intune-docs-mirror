---
layout: Conceptual
title: BitLocker recovery service - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/recovery-service
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
description: Learn about the BitLocker recovery service in Configuration Manager.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: protect
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: fd50f653-19e6-2063-edb0-312d6d5d7762
document_version_independent_id: fd50f653-19e6-2063-edb0-312d6d5d7762
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/recovery-service.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/recovery-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/recovery-service.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 191ce943-047b-6922-c685-66ff68b5379a
---

# BitLocker recovery service - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2103, the implementation of the recovery service changed. It's no longer using legacy MBAM components, but is still conceptually referred to as the *recovery service*. All version 2103 clients use the *message processing engine* component of the management point as their recovery service. They escrow their recovery keys over the secure client notification channel. With this change, you can enable the Configuration Manager site for [enhanced HTTP](../../../core/plan-design/hierarchy/enhanced-http). This configuration doesn't affect the functionality of BitLocker management in Configuration Manager.

When both the site and clients are running Configuration Manager version 2103 or later, clients send their recovery keys to the management point over the secure client notification channel. If any clients are on version 2010 or earlier, they need an HTTPS-enabled recovery service on the management point to escrow their keys.

The BitLocker recovery service is a server component that receives BitLocker recovery data from Configuration Manager clients. The site deploys the recovery service when you create a BitLocker management policy. Configuration Manager automatically installs the recovery service on each management point with an HTTPS-enabled website.

Configuration Manager stores the recovery information in the site database. Without a BitLocker management encryption certificate, Configuration Manager stores the key recovery information in plain text. For more information, see [Encrypt recovery data in the database](encrypt-recovery-data).

Starting in version 2010, you can manage BitLocker policies and escrow recovery keys over a cloud management gateway (CMG). When domain-joined clients communicate via the CMG, they don't use the legacy recovery service, but the message processing engine component of the management point. Microsoft Entra hybrid joined devices also use the message processing engine.

Starting in version 2103, all supported clients use the message processing engine component of the management point as the recovery service. This change reduces dependencies on legacy MBAM components, and enables support for [enhanced HTTP](../../../core/plan-design/hierarchy/enhanced-http).

Note

For version 2010, the message processing engine channel only escrows keys for OS and fixed drive volumes. It doesn't support recovery keys for removable drives or the TPM password hash.

Starting in version 2103, BitLocker management policies over a CMG support the following capabilities:

- Recovery keys for removable drives
- TPM password hash, otherwise known as TPM owner authorization

## Rotate keys

When you recover a key with the self-service or helpdesk portals, since it's disclosed, Configuration Manager requires the client to rotate the key. Rotating the key means that the client generates a new key for BitLocker recovery. It then escrows the new key to the [recovery service](recovery-service).

Note

When you migrate from MBAM, when the device receives a BitLocker management policy from Configuration Manager, it first rotates its key. It then sends the new key to the Configuration Manager recovery service.