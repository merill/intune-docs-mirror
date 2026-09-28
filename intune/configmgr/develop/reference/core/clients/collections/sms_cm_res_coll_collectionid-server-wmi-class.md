---
layout: Conceptual
title: SMS_CM_RES_COLL_CollectionID Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_cm_res_coll_collectionid-server-wmi-class
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
description: The SMS_CM_RES_COLL_CollectionID Windows Management Instrumentation class represents a particular member of an SMS_Collection Server WMI Class object by collection ID.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7519b602-ea99-9b0d-876c-e7ead067a4a7
document_version_independent_id: 49aed745-6faf-ab58-534e-7e02be4c6289
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_cm_res_coll_collectionid-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_cm_res_coll_collectionid-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_cm_res_coll_collectionid-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c79b083-b5fb-6d8f-ec27-14919642242a
---

# SMS_CM_RES_COLL_CollectionID Class - Configuration Manager | Microsoft Learn

The `SMS_CM_RES_COLL_CollectionID` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a particular member of an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object by collection ID.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_RES_COLL_CollectionID : SMS_CollectionMember
{
      UInt32 ClientType;
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
      String Name;
      UInt32 ResourceID;
      UInt32 ResourceType;
      String SiteCode;
      String SMSID;
};
```

## Methods

The `SMS_CM_RES_COLL_CollectionID` class does not define any methods.

## Properties

`ClientType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Type of client. Possible values are:

| Value | Client type |
| --- | --- |
| 1 | Advanced |
| 3 | Device |

`Domain` Data type: `String`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`IsActive` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the collection member is active.

`IsAlwaysInternet` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` to always use the Internet.

`IsApproved` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Whether the resource is approved. Possible values are:

| Value | Approval type |
| --- | --- |
| 0 | Not approved |
| 1 | Approved |
| 2 | Not applicable |

`IsAssigned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`IsBlocked` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the collection member is blocked.

`IsClient` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`IsDecommissioned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the collection member is decommissioned.

`IsDirect` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`IsInternetEnabled` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the collection member is enabled for the Internet.

`IsObsolete` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the collection member is obsolete.

`Name` Data type: `String`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read Only

Qualifiers: [key]

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`ResourceType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`SiteCode` Data type: `String`

Access type: Read Only

Qualifiers: [SizeLimit("3")]

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

`SMSID` Data type: `String`

Access type: Read Only

Qualifiers: None

See [SMS_CollectionMember Server WMI Class](sms_collectionmember-server-wmi-class).

## Remarks

The `CollectionID` property of a collection is the unique collection identifier assigned when the collection is created. The SMS Provider creates several default `SMS_CM_RES_COLL_``CollectionID` classes at installation time for collection IDs with values beginning with "SMS". For example, SMS\_CM\_RES\_COLL\_`SMS00004` identifies all Windows NT Workstation systems.

This class is deleted automatically if the associated collection is deleted.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).