---
layout: Conceptual
title: Migrate from MBAM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/migration-considerations
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
description: Understand the considerations when migrating from Microsoft BitLocker Administration and Monitoring (MBAM) to BitLocker management in Configuration Manager.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: protect
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: 7e9a1056-88c0-9da8-d422-2f3a493234ac
document_version_independent_id: 7e9a1056-88c0-9da8-d422-2f3a493234ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/migration-considerations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/migration-considerations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/migration-considerations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 4ed60860-01e3-8e43-8d38-8a2d398e5ea0
---

# Migrate from MBAM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If you currently use Microsoft BitLocker Administration and Monitoring (MBAM), you can seamlessly migrate management to Configuration Manager. When you deploy BitLocker management policies in Configuration Manager, clients automatically rotate their keys and upload them to the Configuration Manager recovery service.

Important

When you migrate from stand-alone MBAM to Configuration Manager BitLocker management, if you require existing functionality of stand-alone MBAM, don't reuse stand-alone MBAM servers or components with Configuration Manager BitLocker management. If you reuse these servers, stand-alone MBAM will stop working when Configuration Manager BitLocker management installs its components on those servers. Don't run the MBAMWebSiteInstaller.ps1 script to set up the BitLocker portals on stand-alone MBAM servers. When you set up Configuration Manager BitLocker management, use separate servers.

## Group policy

If a group policy setting exists for standalone MBAM, it will override the equivalent setting attempted by Configuration Manager. Standalone MBAM uses domain group policy, while Configuration Manager sets local policies for BitLocker management. Domain policies will override the local Configuration Manager BitLocker management policies. If the standalone MBAM domain group policy doesn't match the Configuration Manager policy, Configuration Manager BitLocker management will fail. For example, if a domain group policy sets the standalone MBAM server for key recovery services, Configuration Manager BitLocker management can't set the same setting for its recovery service. This behavior causes clients to not report their recovery keys to the Configuration Manager BitLocker management recovery service.

Don't set a group policy for a setting that Configuration Manager BitLocker management already specifies. Only set group policies for settings that don't currently exist in Configuration Manager BitLocker management. Configuration Manager has feature parity with standalone MBAM. In most instances there should be no reason to set domain group policies to configure BitLocker policies. To prevent conflicts and problems, avoid use of group policies for BitLocker. Configure all settings through Configuration Manager BitLocker management policies.

## TPM password hash

- Previous MBAM clients don't upload the TPM password hash to Configuration Manager. The client only uploads the TPM password hash once.
- If you need to migrate this information to the Configuration Manager recovery service, clear the TPM on the device. After it restarts, it uploads the new TPM password hash to the recovery service.

Note

Uploading of the TPM password hash mainly pertains to versions of Windows before Windows 10. Windows 10 or later by default doesn't save the TPM password hash, so these devices don't normally upload it. For more information, see [About the TPM owner password](/en-us/windows/security/information-protection/tpm/change-the-tpm-owner-password#about-the-tpm-owner-password).

## Re-encryption

Configuration Manager doesn't re-encrypt drives that are already protected with BitLocker Drive Encryption. If you deploy a BitLocker management policy that doesn't match the drive's current protection, it reports as non-compliant. The drive is still protected.

For example, you used MBAM to encrypt the drive with the AES-XTS 128 encryption algorithm, but the Configuration Manager policy requires AES-XTS 256. The drive is non-compliant with the policy, even though the drive is encrypted.

To work around this behavior, first disable BitLocker on the device. Then deploy a new policy with the new settings.