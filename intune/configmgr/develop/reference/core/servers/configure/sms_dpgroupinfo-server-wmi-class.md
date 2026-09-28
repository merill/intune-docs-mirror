---
layout: Conceptual
title: SMS_DPGroupInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupinfo-server-wmi-class
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
description: An SMS Provider server class that describes a distribution point group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cf1473ab-ae29-6670-2500-64b89370b800
document_version_independent_id: ca29afd5-49f1-0e40-e117-00808b30f441
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpgroupinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 9b1fc3bb-0446-5e0f-2094-2165c1bde8d2
---

# SMS_DPGroupInfo Class - Configuration Manager | Microsoft Learn

The `SMS_DPGroupInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes a distribution point group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupInfo : SMS_BaseClass
{
    UInt32 AssignedContentCount;
    String Description;
    UInt32 FeatureType;
    String GroupID;
    UInt32 MembersCount;
    String Name;
    UInt32 NumberErrors;
    UInt32 NumberInProgress;
    UInt32 NumberSuccess;
    UInt32 NumberUnknown;
};
```

## Methods

The `SMS_DPGroupInfo` class does not define any methods.

## Properties

`AssignedContentCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the packages or applications targeted to this distribution point group.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for this distribution point group.

`FeatureType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Deployment type for monitoring.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique identifier for the distribution point group.

`MembersCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the distribution point members.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the distribution point group.

`NumberErrors` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the number of packages or applications with failed to be distributed to this distribution point.

`NumberInProgress` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the number of packages or applications being distributed to this distribution point.

`NumberSuccess` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the number of packages or applications successfully distributed to this distribution point group.

`NumberUnknown` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the number of packages or applications that are in an unknown state.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).