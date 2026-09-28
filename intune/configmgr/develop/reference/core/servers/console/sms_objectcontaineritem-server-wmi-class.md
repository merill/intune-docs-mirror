---
layout: Conceptual
title: SMS_ObjectContainerItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class
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
description: An SMS Provider server class that contains information about a Configuration Manager console folder item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 18837fc1-4208-3acc-1b50-8445d42c91c0
document_version_independent_id: ab905e5d-573e-d17d-0d23-ecd149b3eae8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 63a4521d-830f-3d95-dd68-ea5eb2d2a6d1
---

# SMS_ObjectContainerItem Class - Configuration Manager | Microsoft Learn

The `SMS_ObjectContainerItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that contains information about a Configuration Manager console folder item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectContainerItem : SMS_BaseClass
{
    UInt32 ContainerNodeID;
    String InstanceKey;
    String MemberGuid;
    UInt32 MemberID;
    UInt32 ObjectType;
    String ObjectTypeName;
    String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_ObjectContainerItem` class.

| Method | Description |
| --- | --- |
| [MoveMembers Method in Class SMS_ObjectContainerItem](movemembers-method-in-class-sms_objectcontaineritem) | Moves one or more folder items to another folder. |
| [MoveMembersEx Method in Class SMS_ObjectContainerItem](movemembersex-method-in-class-sms_objectcontaineritem) | Moves one or more folder items to another folder. |

## Properties

`ContainerNodeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Not\_null]

The unique ID of the folder.

`InstanceKey` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

The name of the folder.

`MemberGuid` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The guid of the relation.

`MemberID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, Not\_null]

The unique ID of the relation.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [deprecated, enumeration, read]

The type of the folder. Possible values are listed below.

| Value | Object type |
| --- | --- |
| 2 | TYPE\_PACKAGE |
| 3 | TYPE\_ADVERTISEMENT |
| 7 | TYPE\_QUERY |
| 8 | TYPE\_REPORT |
| 9 | TYPE\_METEREDPRODUCTRULE |
| 11 | TYPE\_CONFIGURATIONITEM |
| 14 | TYPE\_OSINSTALLPACKAGE |
| 17 | TYPE\_STATEMIGRATION |
| 18 | TYPE\_IMAGEPACKAGE |
| 19 | TYPE\_BOOTIMAGEPACKAGE |
| 20 | TYPE\_TASKSEQUENCEPACKAGE |
| 21 | TYPE\_DEVICESETTINGPACKAGE |
| 23 | TYPE\_DRIVERPACKAGE |
| 25 | TYPE\_DRIVER |
| 1011 | TYPE\_SOFTWAREUPDATE |
| 2011 | TYPE\_CONFIGURATIONBASELINE |
| 5000 | TYPE\_DEVICE\_COLLECTION |
| 5001 | TYPE\_USER\_COLLECTION |

`ObjectTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The WMI Class Name of the object. Example SMS\_Package. This will take effect if the ObjectType is 0 or null.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The sitecode of the site that the relation was originally created from.

## Remarks

When attempting to move an item from a root node such as a user collection or device collection, the item doesn't exist as an SMS\_ObjectContainerItem. As such a new instance will need to be created instead.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).