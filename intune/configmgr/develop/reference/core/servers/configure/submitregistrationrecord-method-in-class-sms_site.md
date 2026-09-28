---
layout: Conceptual
title: SubmitRegistrationRecord Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site
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
description: A Windows Management Instrumentation class method that submits a registration record.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fa0f4203-7287-704b-ec9f-bc9d8aa2cbd4
document_version_independent_id: 5d23c917-aae9-b224-e2f1-b7f6c7c9a319
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54e026d3-4626-abee-e772-525f02c96dbd
---

# SubmitRegistrationRecord Method - Configuration Manager | Microsoft Learn

The `SubmitRegistrationRecord` Windows Management Instrumentation (WMI) class method, in Configuration Manager, submits a registration record.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 SubmitRegistrationRecord(
     String SMSID,
     String Certificate,
     String CertificatePFX,
     SInt32 Type,
     String ServerName,
     SInt32 UdaSetting,
     SInt32 IssuedCert
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: [in]

The GUID used to identify the certificate. This is the value of the `SMSID` property in [SMS_CertificateInfo Server WMI Class](../../../osd/sms_certificateinfo-server-wmi-class).

`Certificate` Data type: `String`

Qualifiers: [in]

Hexadecimal-encoded certificate.

`CertificatePFX` Data type: `String`

Qualifiers: [in, optional]

Hexadecimal-encoded private key for PFX file containing the certificate. The default value is "".

`Type` Data type: `SInt32`

Qualifiers: [in, optional]

The type of certificate. Possible values are defined for the `Type` property of [SMS_CertificateInfo Server WMI Class](../../../osd/sms_certificateinfo-server-wmi-class). The default value for this parameter is BootMedia (1).

`ServerNam` Data type: `String`

Qualifiers: [in, optional]

Name used to identify the server.

`UdaSetting` Data type: `SInt32`

Qualifiers: [in, optional]

UdaSetting. The default value for this parameter is Disabled (0).

| Value | UdaSetting |
| --- | --- |
| 0 | Disabled |
| 1 | Pending |
| 2 | Auto |

`IssuedCert` Data type: `SInt32`

Qualifiers: [in, optional]

IssuedCert. . The default value for this parameter is 1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).