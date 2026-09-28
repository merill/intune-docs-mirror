---
layout: Conceptual
title: SMS_ClientPfxCertificate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class
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
description: The SMS_ClientPfxCertificate Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that contains an imported  Pfx certificate.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4bcb1d67-fcf7-7dab-651a-2959ca8a9c94
document_version_independent_id: 1173ad83-fee3-1257-1b72-24487f00ba40
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9f9d06e-9a1b-b617-3294-d538b9f16a2d
---

# SMS_ClientPfxCertificate Class - Configuration Manager | Microsoft Learn

The `SMS_ClientPfxCertificate` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains an imported Pfx certificate.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientPfxCertificate : SMS_BaseClass
{
    UInt32 CI_ID;
    UInt32 DeviceID;
    UInt32 IsTombstoned;
    String ProfileName;
    String Thumbprint;
    UInt32 UserItemKey;
    String UserName;
    DateTime ValidFrom;
    DateTime ValidUntil;
};

```

## Methods

The following table lists the methods in the `SMS_ClientPfxCertificate` class.

| Method | Description |
| --- | --- |
| [ImportForUser Method in Class SMS_ClientPfxCertificate](importforuser-method-in-class-sms_clientpfxcertificate) | Imports a certificate for a user, encrypted by using a password. |
| [DeleteForUser Method in Class SMS_ClientPfxCertificate](deleteforuser-method-in-class-sms_clientpfxcertificate) | Deletes a certificate for a user. |

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The unique ID of the configuration item.

`DeviceID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The ID of the device.

`IsTombstoned` Data type: `UInt32`

Access type: Read

Qualifiers: none

Specifies whether the certificate is marked for deletion.

`ProfileName` Data type: `String`

Access type: Read

Qualifiers: [key]

An SMS\_ConfigurationPolicy Profile unique ID.

`Thumbprint` Data type: `String`

Access type: Read

Qualifiers: [key]

The thumbprint for the certificate.

`UserItemKey` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The user item key.

`UserName` Data type: `String`

Access type: Read

Qualifiers: [key]

The user name.

`ValidFrom` Data type: `DateTime`

Access type: Read

Qualifiers: none

The start date for the certificate.

`ValidUntil` Data type: `DateTime`

Access type: Read

Qualifiers: none

The expiration date for the certificate.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).