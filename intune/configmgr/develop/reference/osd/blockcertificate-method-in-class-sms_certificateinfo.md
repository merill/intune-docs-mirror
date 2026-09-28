---
layout: Conceptual
title: BlockCertificate Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo
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
description: The BlockCertificate Windows Management Instrumentation (WMI) class method, in Configuration Manager, blocks or unblocks the specified certificate.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dbd37f48-772d-e150-9eea-ef4ce5d84690
document_version_independent_id: 61b37659-2093-5c7b-4f64-95977b14d130
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e89ebe22-d7fd-cd7d-6542-9618bd8d1660
---

# BlockCertificate Method - Configuration Manager | Microsoft Learn

The `BlockCertificate` Windows Management Instrumentation (WMI) class method, in Configuration Manager, blocks or unblocks the specified certificate.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 BlockCertificate(
      String SMSID,
      Boolean Blocked
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: [in]

The GUID used to identify the certificate. This identifier is defined by the `SMSID` property of [SMS_CertificateInfo Server WMI Class](sms_certificateinfo-server-wmi-class).

`Blocked` Data type: `Boolean`

Qualifiers: [in]

`true`, by default, to block the certificate. A blocked certificate is rejected by the site database. See the Remarks section later in this topic.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

The value furnished for the `Blocked` parameter directly affects the setting of the `IsBlocked` property of [SMS_CertificateInfo Server WMI Class](sms_certificateinfo-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).