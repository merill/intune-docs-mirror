---
layout: Conceptual
title: SMS_CertificateData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificatedata-server-wmi-class
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
description: Learn how to represent certificate data managed by Configuration Manager using SMS_CertificateData class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 18081d86-f2ce-eef0-5887-34da88b9e446
document_version_independent_id: 24606227-988d-6d69-f58c-a48261d09c3c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_certificatedata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_certificatedata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_certificatedata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e5240c93-1f8a-df04-2961-64350d16b505
---

# SMS_CertificateData Class - Configuration Manager | Microsoft Learn

The `SMS_CertificateData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents certificate data managed by Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CertificateData : SMS_BaseClass
{
    String CertID;
    UInt32 CertType;
    String Description;
    String Name;
};
```

## Methods

The following table lists the methods in the `SMS_CertificateData` class.

| Method | Description |
| --- | --- |
| [SubmitCertificate Method in Class SMS_CertificateData](submitcertificate-method-in-class-sms_certificatedata) | Submit certificate. |
| [DeleteCertificate Method in Class SMS_CertificateData](deletecertificate-method-in-class-sms_certificatedata) | Deletes the certificate from the database. |

## Properties

`CertID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Certificate unique identifier.

`CertType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Certificate type. Possible values are:

| Value | Certificate type |
| --- | --- |
| 1 | Windows Intune Subscription |

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Certificate description.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Certificate name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).