---
layout: Conceptual
title: SMS_SearchFolder Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_searchfolder-server-wmi-class
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
description: Learn how to use SMS_SearchFolder WMI class in Configuration Manager to perform search operations.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e3fde785-dc7e-2679-7bf3-8e381fa496e6
document_version_independent_id: 4b069523-aaec-7e84-324d-5b4003728e8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/sms_searchfolder-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/sms_searchfolder-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/sms_searchfolder-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: c82d6105-ceb6-4c34-cfd1-2a16d91927d6
---

# SMS_SearchFolder Class - Configuration Manager | Microsoft Learn

The `SMS_SearchFolder` WMI class is an SMS Provider server class, in Configuration Manager, that behaves the same as `SMS_ObjectContainerNode`, but is only used for search operations.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SearchFolder : SMS_BaseClass
{
   UInt32 FolderId;
   String GroupID;
   Boolean IsSystem;
   String Name;
   UInt32 ObjectType;
   String SearchString;
   String SourceSite;
};
```

## Methods

The `SMS_SearchFolder` class does not define any methods.

## Properties

`FolderId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The unique ID of this search folder.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Group ID of the search folder.

`IsSystem` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

A flag that indicates whether this is a system folder.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Folder name. Default value is New Folder.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of the folder.

`SearchString` Data type: `String`

Access type: Read/Write

Qualifiers: None

Search string get/set by AdminConsole.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The sidecode of the site that the folder originated from.

## Remarks

In Configuration Manager, the search folder and folders were one class. Now, in Configuration Manager, they are separate classes. `SMS_SearchFolders` folders appear in the "Manage Searches" class of menus in the console. The `SMS_SearchFolders` folders have no dedicated node and are used for node searches only. `SMS_SearchFolders` folders cannot be used for global searches.

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).