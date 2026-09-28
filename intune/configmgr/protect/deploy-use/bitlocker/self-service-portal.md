---
layout: Conceptual
title: BitLocker self-service portal - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/self-service-portal
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
description: How to use the user self-service portal in Configuration Manager for BitLocker recovery
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 93810223-d31d-28a4-8f79-22b779e9e589
document_version_independent_id: c735c163-6f1a-ffa1-096c-1429c643ee50
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/self-service-portal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/self-service-portal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/self-service-portal.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: be878417-ff30-4214-8e69-311d35eb9ca2
---

# BitLocker self-service portal - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you [install the BitLocker self-service portal](setup-websites), if BitLocker locks a user's device, they can independently get access to their computers. The self-service portal requires no assistance from help desk staff.

[![Screenshot of default BitLocker self-service portal](media/bitlocker-self-service-portal.png)](media/bitlocker-self-service-portal.png#lightbox)

Important

To get a recovery key from the self-service portal, a user must have successfully signed in to the computer at least once. This sign-in must be local to the device, not in a remote session. Otherwise, they need to contact the help desk for key recovery. A help desk administrator can use the [administration and monitoring website](helpdesk-portal) to request the recovery key.

BitLocker can lock the device in the following situations:

- The user forgets their BitLocker password or PIN
- There's a change to the device's OS files, BIOS, or Trusted Platform Module (TPM)

To request the BitLocker recovery key from the self-service portal:

1. When BitLocker locks a device, it displays the BitLocker recovery screen during startup. Write down the 32-digit BitLocker recovery key ID.
2. On another computer, go to the self-service portal in the web browser, for example `https://webserver.contoso.com/SelfService`.
3. Read and accept the notice.
4. In the **Recovery Key ID** field, enter the first eight digits of the BitLocker recovery key ID. If it matches multiple keys, then enter all 32 digits.
5. Choose one of the following options for the **Reason** for this request:

    - BIOS/TPM changed
    - OS filed modified
    - Lost PIN/passphrase
6. Select **Get Key**. The self-service portal displays the 48-digit **BitLocker recovery key**.
7. Enter this 48-digit code into the BitLocker recovery screen on your computer.

Note

The BitLocker self-service portal may timeout after a period of inactivity. For example, after five minutes you may see a timeout warning with a 60 second counter.

![BitLocker self-service portal timeout warning](media/bitlocker-self-service-portal-timeout-warning.png)

If you don't respond to the countdown, the session will expire.

![BitLocker self-service portal session expired page](media/bitlocker-self-service-portal-session-expired.png)