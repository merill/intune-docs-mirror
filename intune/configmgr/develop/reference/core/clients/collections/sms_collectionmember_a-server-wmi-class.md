---
layout: Conceptual
title: SMS_CollectionMember_a Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionmember_a-server-wmi-class
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
description: In Configuration Manager, the SMS_CollectionMember_a association WMI class is an SMS Provider server class that relates an SMS_Collection Server WMI Class object with SMS_Resource Server WMI Class objects that represent the member resources of the collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c0a6b246-99a1-6539-9699-b8b30c1ec2a6
document_version_independent_id: e4d0eb76-8f20-bc77-d871-2a8359e22959
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionmember_a-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionmember_a-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionmember_a-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 165de916-7c6b-45bf-8819-a44966c8a428
---

# SMS_CollectionMember_a Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionMember_a` association Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object with [SMS_Resource Server WMI Class](../manage/sms_resource-server-wmi-class) objects that represent the member resources of the collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionMember_a : SMS_BaseAssociation
{
      UInt32 ClientCertType;
      UInt32 ClientType;
      ref:SMS_Collection collection;
      String CollectionID;
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
      String Name;
      ref:SMS_Resource resource;
      UInt32 ResourceID;
      UInt32 ResourceType;
      String SiteCode;
      String SMSID;
      Boolean IsVirtualMachine;
};
```

## Methods

The `SMS_CollectionMember_a` class does not define any methods.

## Properties

`ClientCertType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client certificate type. Possible values are:

| Value | Client certificate type |
| --- | --- |
| 1 | Self-signed certificate |
| 2 | Certificate issued by a certification authority. |

`ClientType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Type of client. Possible values are:

| Value | Client type |
| --- | --- |
| 1 | Client |
| 3 | Device |

`Collection` Data type: `ref:SMS_Collection`

Access type: Read Only

Qualifiers: [key]

Reference to an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object path.

`CollectionID` Data type: `String`

Access type: Read Only

Qualifiers: None

ID of the collection.

`DeviceOwner` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Owner of the device.

| Value | Device owner |
| --- | --- |
| 1 | Company |
| 2 | Personal |

`Domain` Data type: `String`

Access type: Read Only

Qualifiers: None

Windows NT or Windows 2000 domain to which the resource belongs.

`IsActive` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is active.

`IsAlwaysInternet` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is always associated with the Internet.

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

`true` if the resource is within the site boundaries and has been assigned to the site.

`IsBlocked` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is blocked.

`IsClient` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client software has been installed on the resource.

`IsDecommissioned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is decommissioned.

`IsDirect` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is a member of the associated collection by a direct rule. For more information, see [SMS_CollectionRuleDirect Server WMI Class](sms_collectionruledirect-server-wmi-class).

`IsInternetEnabled` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is Internet-enabled.

`IsObsolete` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is obsolete.

`IsVirtualMachine` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a virtual machine.

`Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Name of the member resource.

`resource` Data type: `ref:SMS_Resource`

Access type: Read Only

Qualifiers: [key]

Reference to an [SMS_Resource Server WMI Class](../manage/sms_resource-server-wmi-class) object path.

`ResourceID` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

The identifier of the member resource.

`ResourceType` Data type: `Uint32`

Access type: Read Only

Qualifiers: None

Type of the member resource as defined by instances of [SMS_ResourceMap Server WMI Class](../manage/sms_resourcemap-server-wmi-class).

`SiteCode` Data type: `String`

Access type: Read Only

Qualifiers: [SizeLimit("3")]

Site code of the site with which the resource is associated.

`SMSID` Data type: `String`

Access type: Read Only

Qualifiers: None

Configuration Manager unique ID of the member resource.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    The `CollectionID` and `ResourceID` properties can be used in a WMI Query Language (WQL) WHERE clause. However, you are limited to using an OR condition. Your query might not use the other properties in the relationship.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).