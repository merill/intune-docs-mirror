---
layout: Conceptual
title: Certificate profile security and privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/security-and-privacy-for-certificate-profiles
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
description: Learn about the security guidance for managing certificate profiles for users and devices in Configuration Manager.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: fd19011d-606b-9e2d-2937-30393dbcc8c2
document_version_independent_id: 44e8c457-548a-166c-c9f4-3e2db19e5c9e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/security-and-privacy-for-certificate-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/security-and-privacy-for-certificate-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/security-and-privacy-for-certificate-profiles.md
cmProducts: []
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5e8ad6db-8b8c-452c-b81a-f285ec58edd4
platformId: ac7b3b6b-7aab-2953-73b3-d35c4387ea06
---

# Certificate profile security and privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](resource-access-deprecation-faq).

## Security guidance

Use the following guidance when you manage certificate profiles for users and devices.

### Follow security guidance for the Network Device Enrollment Service (NDES)

Identify and follow any security guidance for NDES. For example, configure the NDES website in Internet Information Services (IIS) to require HTTPS and ignore client certificates.

For more information, see [Network Device Enrollment Service Guidance](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498%28v=ws.11%29).

### Choose the most secure options for certificate profiles

When you configure SCEP certificate profiles, choose the most secure options that devices and your infrastructure can support. Identify, implement, and follow any security guidance that's recommended for your devices and infrastructure.

### Centrally specify user device affinity

Manually specify user device affinity instead of allowing users to identify their primary device. Don't enable usage-based configuration.

If you use the option in a SCEP certificate profile to **Allow certificate enrollment only on the users primary device**, don't consider the information that's collected from users or from the device to be authoritative. If you deploy SCEP certificate profiles with this configuration, and a trusted administrative user doesn't specify user device affinity, unauthorized users might receive elevated privileges and be granted certificates for authentication.

Note

If you do enable usage-based configuration, this information is collected by using state messages. Configuration Manager doesn't secure state messages. To help mitigate this threat, use SMB signing or IPsec between client computers and the management point.

### Manage certificate template permissions

Don't add **Read** and **Enroll** permissions for users to the certificate templates. Don't configure the certificate registration point to skip the certificate template check.

Configuration Manager supports the extra check if you add the security permissions of **Read** and **Enroll** for users. If authentication isn't possible, you can configure the certificate registration point to skip this check. But neither configuration is recommended.

For more information, see [Planning for certificate template permissions for certificate profiles](planning-for-certificate-template-permissions).

## Privacy information

You can use certificate profiles to deploy root certification authority (CA) and client certificates, and then evaluate whether those devices become compliant after the client applies the profiles. The management point sends compliance information to the site server, and Configuration Manager stores that information in the site database. Compliance information includes certificate properties such as subject name and thumbprint. The client encrypts this information when sent to the management point, but the site database doesn't store it in an encrypted format. Compliance information isn't sent to Microsoft.

Certificate profiles use information that Configuration Manager collects using discovery. For more information, see [Privacy information for discovery](../../core/plan-design/hierarchy/security-and-privacy-for-site-administration#BKMK_Privacy_Cliients).

By default, devices don't evaluate certificate profiles. You need to configure the certificate profiles, and then deploy them to users or devices.

Note

Certificates that are issued to users or devices might allow access to confidential information.