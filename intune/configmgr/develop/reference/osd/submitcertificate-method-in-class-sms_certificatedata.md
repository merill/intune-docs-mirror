---
layout: Conceptual
title: SubmitCertificate Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/submitcertificate-method-in-class-sms_certificatedata
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
description: The SubmitCertificate Windows Management Instrumentation (WMI) class method in Configuration Manager submits the specified certificate.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a990efba-6899-6f3f-9bf4-cea154d84508
document_version_independent_id: a284b051-ddf2-daae-56c0-d1c59995cdc4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/submitcertificate-method-in-class-sms_certificatedata.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/submitcertificate-method-in-class-sms_certificatedata
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/submitcertificate-method-in-class-sms_certificatedata.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0ca8caef-10cf-b360-2bc0-a902598a8605
---

# SubmitCertificate Method - Configuration Manager | Microsoft Learn

The `SubmitCertificate` Windows Management Instrumentation (WMI) class method in Configuration Manager that submits the specified certificate.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 SubmitCertificate
{
    [IN]    UInt32 CertType
    [IN]    UInt8 CertData[]
    [IN]    UInt8 Password[]
    [IN]    String Name
    [IN]    String Description
};
```

## Parameters

`CertType` Data type: `UInt32`

Qualifiers: [id("0"), in]

Required. Certificate type. Possible values are:

| Value | Certificate type |
| --- | --- |
| 1 | Windows Intune Subscription |

`CertData` Data type: `UInt8 Array`

Qualifiers: [id("1"), in]

Required. Certificate PFX data.

`Password` Data type: `UInt8 Array`

Qualifiers: [id("2"), in, optional]

Optional. Password to read the certificate PFX data.

`Name` Data type: `String`

Qualifiers: [id("3"), in, optional]

Optional. Certificate name.

`Description` Data type: `String`

Qualifiers: [id("4"), in, optional]

Optional. Certificate description.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).