---
layout: Conceptual
title: SMS_FullCollectionMembership Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_fullcollectionmembership-server-wmi-class
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
description: Learn how to use the SMS_FullCollectionMembership class in Configuration Manager to list all member resources for a specific collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 93dc96b3-8913-951d-b640-ee2cc815d0b7
document_version_independent_id: 87c40d5b-53fd-9fe8-d31f-bc10888b2f2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_fullcollectionmembership-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_fullcollectionmembership-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_fullcollectionmembership-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c30551e-1b7a-346d-e994-79dc48e100f5
---

# SMS_FullCollectionMembership Class - Configuration Manager | Microsoft Learn

The `SMS_FullCollectionMembership` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists all member resources of a specific collection.

## Syntax

```
Class SMS_FullCollectionMembership : SMS_BaseClass
{
      UInt32 ClientCertType;
      UInt32 ClientType;
      String ClientVersion;
      String CollectionID;
      String DeviceCategory;
      UInt32 DeviceOwner;
      String Domain;
      Boolean IsActive;
      Boolean IsAlwaysInternet;
      UInt32 IsApproved;
      Boolean IsAssigned;
      Boolean IsBlocked;
      Boolean IsClient;
      Boolean IsDecommissioned;
      Boolean IsDirect;
      Boolean IsInternetEnabled;
      Boolean IsObsolete;
      Boolean IsVirtualMachine;
      String Name;
      UInt32 Priority;
      UInt32 ResourceID;
      UInt32 ResourceType;
      String SiteCode;
      String SMSID;
};
```

## Methods

The `SMS_FullCollectionMembership` class does not define any methods.

## Properties

`ClientCertType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client certificate type. Possible values are:

- Self-signed Certificate
- PKI Certificate

`ClientType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Type of client. Possible values are:

| Value | Definition |
| --- | --- |
| 1 | Client |
| 3 | Device |

`ClientVersion` Data type: `String`

Access type: Read/Write

Qualifiers: none

Version of the installed client software.

`CollectionID` Data type: `String`

Access type: Read Only

Qualifiers: [key]

ID of the collection to which the member belongs.

`DeviceCategory` Data type: `String`

Access type: Read/Write

Qualifiers: none

Category of the device.

`DeviceOwner` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Owner of the device. Possible values are:

| Value | Definition |
| --- | --- |
| 1 | Company |
| 2 | Personal |

`Domain` Data type: `String`

Access type: Read Only

Qualifiers: None

Domain to which the resource belongs.

`IsActive` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is active.

`IsAlwaysInternet` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if this is an Internet-facing client.

`IsApproved` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Whether the resource is approved. Possible values are:

| Value | Definition |
| --- | --- |
| 0 | Not approved |
| 1 | Approved |
| 2 | Not applicable |

`IsAssigned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is assigned to any site.

`IsBlocked` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is blocked.

`IsClient` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if this is a client.

`IsDecommissioned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the record is deleted.

`IsDirect` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is a member through a direct rule, represented by [SMS_CollectionRuleDirect Server WMI Class](sms_collectionruledirect-server-wmi-class); otherwise `false` or `null`.

`IsInternetEnabled` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client can be Internet-enabled.

`IsObsolete` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if this is an obsolete record.

`IsVirtualMachine` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a virtual machine.

`Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Name of the resource.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Priority of the client settings.

`ResourceID` Data type: `UInt32`

Access type: Read Only

Qualifiers: [key]

Unique ID supplied by Configuration Manager for the resource. This ID is not unique across sites.

`ResourceType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Type of resource. Possible values are:

- System
- User groups
- User

    `SiteCode` Data type: `String`

    Access type: Read Only

    Qualifiers: [SizeLimit("3")]

    Site code of the site that created the collection.

    `SMSID` Data type: `String`

    Access type: Read Only

    Qualifiers: None

    Configuration Manager unique ID.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).