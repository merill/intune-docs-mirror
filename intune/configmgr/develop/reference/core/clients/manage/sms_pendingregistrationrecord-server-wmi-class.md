---
layout: Conceptual
title: SMS_PendingRegistrationRecord Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_pendingregistrationrecord-server-wmi-class
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
description: Learn how to use the SMS_PendingRegistrationRecord Windows Management Instrumentation (WMI) class, in Configuration Manager, that describes hardware conflicts between two computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 19764cfb-48bc-1dc5-3485-d1d9cd8b335d
document_version_independent_id: 388a1484-5f77-0837-37f0-534a58d44b16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_pendingregistrationrecord-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_pendingregistrationrecord-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_pendingregistrationrecord-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 68c7b03c-c2f7-262f-4988-c8944282c2f5
---

# SMS_PendingRegistrationRecord Class - Configuration Manager | Microsoft Learn

The `SMS_PendingRegistrationRecord` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes hardware conflicts between two computers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PendingRegistrationRecord
{
      string AgentName;
      string Certificate;
      string ClientVersion;
      string ConflictSMSID;
      string FQDN;
      string HardwareID;
      boolean IsAlwaysInternet;
      boolean IsIntegratedAuth;
      boolean IsInternetEnabled;
      string IssuedTo;
      sint32 KeyType;
      string NetBiosName;
      string PublicKey;
      string SiteCode;
      string SMSID;
      string Thumbprint;
      datetime ValidFrom;
      datetime ValidUntil;
};
```

## Methods

The following table lists the methods in the `SMS_PendingRegistrationRecord` class.

| Method | Description |
| --- | --- |
| [ResolvePendingRegistrationRecord Method in Class SMS_PendingRegistrationRecord](resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord) | Resolves the conflicts for the pending registration records. |

## Properties

`AgentName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The internal agent name of the client.

`Certificate` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

The encoded certificate of the client.

`ClientVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The version of the installed client.

`ConflictSMSID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Configuration Manager unique identifier of a client that registered on the current site with the same `HardwareID`

`FQDN` Data type: `String`

Access type: Read/Write

Qualifiers: None

The fully qualified domain name of the computer.

`HardwareID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The calculated hardware identifier of the computer this client belongs to.

`IsAlwaysInternet` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the resource is always associated with the Internet.

`IsIntegratedAuth` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if integrated authentication is enabled.

`IsInternetEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if this client is an Internet-facing client.

`IssuedTo` Data type: `String`

Access type: Read/Write

Qualifiers: None

The certificate subject name.

`KeyType` Data type: `Sint32`

Access type: Read/Write

Qualifiers: enumeration("self-sign(1), issued (2)")

Public key type of certificate. The following values are possible.

| Value | Description |
| --- | --- |
| 1 | Self-signed certificate. |
| 2 | Certificate was issued by a certification authority. |

`NetBiosName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The NetBIOS name of the computer.

`PublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: lazy

The public key of the certificate, which reflects the globally unique SHA-1 hash thumbprint indicated by the `Thumbprint` property.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Configuration Manager site this client belongs to.

`SMSID` Data type: `String`

Access type: Read/Write

Qualifiers: key

The unique identifier of the client that sent the pending registration record.

`Thumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: Lazy

The hash value of the certificate.

`ValidFrom` Data type: `Datetime`

Access type: Read/Write

Qualifiers: None

The date and time when the certificate becomes effective.

`ValidUntil` Data type: `Datetime`

Access type: Read/Write

Qualifiers: None

The date and time when the certificate expires.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).