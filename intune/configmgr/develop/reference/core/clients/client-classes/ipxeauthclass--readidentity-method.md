---
layout: Conceptual
title: IPxeAuthClass::ReadIdentity - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method
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
description: Learn how to use the Configuration Manager with the CreateIdentity method to create a PXE certificate identity that is used in the client configuration file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d3cd13a2-7240-3da9-b226-3cf1845d93e8
document_version_independent_id: 8143f9bc-6efc-06f5-b9f5-52bc32eea604
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method.md
cmProducts: []
platformId: cd4062f8-49f3-c0d5-eb86-fc60f101ce66
---

# IPxeAuthClass::ReadIdentity - Configuration Manager | Microsoft Learn

In Configuration Manager, the `ReadIdentity` method reads a PXE certificate identity from the client configuration (PFX) file. The method is used in serializing a certificate from the file.

## Syntax

```
HRESULT ReadIdentity(
   BSTR FileName,
   BSTR FilePassword,
   BSTR SMSID,
   VARIANT* Identity
);
```

#### Parameters

`FileName` Data type: `BSTR`

Qualifiers: [in]

Name of the client configuration (PFX) file.

`FilePassword` Data type: `BSTR`

Qualifiers: [in]

Password to use for access to the client configuration file.

`SMSID` Data type: `BSTR`

Qualifiers: [in]

The GUID used to identify the certificate. This is the value of the SMSID property in [SMS_CertificateInfo Server WMI Class](../../../osd/sms_certificateinfo-server-wmi-class).

`Identity` Data type: `VARIANT`

Qualifiers: [out, retval]

PXE certificate identity. The return value can be used with [SubmitRegistrationRecord Method in Class SMS_Site](../../servers/configure/submitregistrationrecord-method-in-class-sms_site).

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.

## Remarks