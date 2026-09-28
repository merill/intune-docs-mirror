---
layout: Conceptual
title: IPxeAuthClass::CreateIdentity - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method
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
description: Learn how to use the CreateIdentity method to create a new self-signed certificate.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f904e699-d712-68e9-62ce-f2bc68ad5964
document_version_independent_id: e68607a4-6e07-a592-262c-f832d097e853
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method.md
cmProducts: []
platformId: 92fbb85c-0f86-5d66-3b7b-cd48bc518d52
---

# IPxeAuthClass::CreateIdentity - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CreateIdentity` method creates a PXE certificate identity that is used in the client configuration file. This method is used to create a new self-signed certificate.

## Syntax

```
HRESULT CreateIdentity(
      BSTR FriendlyName,
      BSTR SubjectName,
      BSTR SMSID,
      VARIANT* StartTime,
      VARIANT* EndTime,
      VARIANT* Identity
);
```

#### Parameters

`FriendlyName` Data type: `BSTR`

Qualifiers: [in]

Friendly name of the certificate identity.

`SubjectName` Data type: `BSTR`

Qualifiers: [in]

Name of the certificate subject.

`SMSID` Data type: `BSTR`

Qualifiers: [in]

The GUID used to identify the certificate. This is the value of the SMSID property in [SMS_CertificateInfo Server WMI Class](../../../osd/sms_certificateinfo-server-wmi-class).

`StartTime` Data type: `VARIANT`

Qualifiers: [in]

Time when the certificate becomes valid.

`EndTime` Data type: `VARIANT`

Qualifiers: [in]

Time when the validity of the certificate ends.

`Identity` Data type: `VARIANT`

Qualifiers: [out, retval]

PXE certificate identity. Can be used with [SubmitRegistrationRecord Method in Class SMS_Site](../../servers/configure/submitregistrationrecord-method-in-class-sms_site).

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.

## Remarks