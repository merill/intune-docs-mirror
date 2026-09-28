---
layout: Conceptual
title: SMS_CertificateInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class
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
description: The SMS_CertificateInfo WMI class is an SMS Provider server class, in Configuration Manager, that defines a media certificate registered by Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1123e85e-b9a3-6235-fa29-b99d1f9bc8ca
document_version_independent_id: d8ee3502-a54d-383f-8499-8f58b042cc66
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6575b3fd-4ecd-548f-b8e8-5fccdf5be434
---

# SMS_CertificateInfo Class - Configuration Manager | Microsoft Learn

The `SMS_CertificateInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that defines a media certificate registered by Configuration Manager and used by client computers to communicate with a management point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CertificateInfo : SMS_BaseClass
{
      String Certificate;
      Boolean IsApproved;
      Boolean IsBlocked;
      String IssuedTo;
      SInt32 KeyType;
      String PublicKey;
      String SMSID;
      String Thumbprint;
      UInt32 Type;
      DateTime ValidFrom;
      DateTime ValidUntil;
};
```

## Methods

The following table shows the methods in `SMS_CertificateInfo`.

| Name | Description |
| --- | --- |
| [BlockCertificate Method in Class SMS_CertificateInfo](blockcertificate-method-in-class-sms_certificateinfo) | Blocks or unblocks the specified certificate. |

## Properties

`Certificate` Data type: `String`

Access type: Read/Write

Qualifiers: [large, lazy]

The certification content.

`IsApproved` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the certificate is approved.

`IsBlocked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the certificate is blocked. A blocked certificate is rejected by the site database. See the [BlockCertificate Method in Class SMS_CertificateInfo](blockcertificate-method-in-class-sms_certificateinfo).

`IssuedTo` Data type: `String`

Access type: Read/Write

Qualifiers: None

The identity of the client.

`KeyType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

The public key type for the certificate. Possible values are:

| Value | Key type |
| --- | --- |
| 1 | self-sign |
| 2 | issued |

`PublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Public key of the certificate, which reflects the globally unique SHA-1 hash thumbprint indicated by the `Thumbprint` property.

`SMSID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The GUID used to identify the certificate.

`Thumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: [Lazy]

Hash value of the certificate.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of certificate. Possible values are:

| Value | Certificate type |
| --- | --- |
| 1 | Boot Media |
| 2 | PXE |
| 3 | ISVProxy |

`ValidFrom` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the certificate becomes effective.

`ValidUntil` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the certificate expires.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).