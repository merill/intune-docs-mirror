---
layout: Conceptual
title: Non-compliance codes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/non-compliance-codes
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
description: A technical reference for the possible codes from a Configuration Manager client that's not compliant with BitLocker policy
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7fb48285-698b-3930-f279-61624cd06cba
document_version_independent_id: 8fdac2bd-9b1b-fad3-4657-6892b0e836c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/tech-ref/bitlocker/non-compliance-codes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/tech-ref/bitlocker/non-compliance-codes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/tech-ref/bitlocker/non-compliance-codes.md
cmProducts: []
platformId: f03b216d-7fab-cb69-ec4d-cbe0a5420823
---

# Non-compliance codes - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

WMI on the client provides the following non-compliance codes. It also describes the reasons why a particular device reports as non-compliant.

There are various methods to view WMI. For example, use the following PowerShell command:

```PowerShell
(Get-WmiObject -Class mbam_Volume -Namespace root\microsoft\mbam).ReasonsForNoncompliance
```

Tip

If the device is compliant, this command doesn't return anything.

You can also check the `Compliant` attribute of this class, which is `1` if the device is compliant.

| Non-compliance code | Reason for non-compliance |
| --- | --- |
| 0 | Cipher strength not AES 256. |
| 1 | BitLocker policy requires this volume to be encrypted, but it isn't. |
| 2 | BitLocker policy requires this volume to *not* be encrypted, but it is. |
| 3 | BitLocker policy requires this volume use a TPM protector, but it doesn't. |
| 4 | BitLocker policy requires this volume use a TPM+PIN protector, but it doesn't. |
| 5 | BitLocker policy doesn't allow non-TPM machines to report as compliant. |
| 6 | Volume has a TPM protector, but the TPM isn't visible. |
| 7 | BitLocker policy requires this volume use a password protector, but it doesn't have one. |
| 8 | BitLocker policy requires this volume *not* use a password protector, but it has one. |
| 9 | BitLocker policy requires this volume use an auto-unlock protector, but it doesn't have one. |
| 10 | BitLocker policy requires this volume *not* use an auto-unlock protector, but it has one. |
| 11 | BitLocker detects a policy conflict, which prevents it from reporting this volume as compliant. |
| 12 | A system volume is needed to encrypt the OS volume, but it isn't present. |
| 13 | Protection is suspended for the volume. |
| 14 | Auto-unlock protector is unsafe unless the OS volume is encrypted. |
| 15 | Policy requires minimum cypher strength is XTS-AES-128 bit, actual cypher strength is weaker. |
| 16 | Policy requires minimum cypher strength is XTS-AES-256 bit, actual cypher strength is weaker. |