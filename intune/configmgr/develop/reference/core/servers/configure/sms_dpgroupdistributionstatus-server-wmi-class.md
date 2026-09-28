---
layout: Conceptual
title: SMS_DPGroupDistributionStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatus-server-wmi-class
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
description: Learn how the SMS_DPGroupDistributionStatus Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes distribution information for a given distribution point group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9c006968-23e8-5d7a-0ab6-dd8feada0f84
document_version_independent_id: 10accc79-bdf2-b33f-be3b-9fd0b1e67b8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 66635cb1-53ca-6480-d745-fa9876e015e7
---

# SMS_DPGroupDistributionStatus Class - Configuration Manager | Microsoft Learn

The `SMS_DPGroupDistributionStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes distribution information for a given distribution point group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupDistributionStatus : SMS_BaseClass
{
    UInt32 Assets;
    UInt32 ContentCount;
    String GroupID;
    UInt32 MessageCategory;
    UInt32 MessageType;
    DateTime StatusTime;
};
```

## Methods

The `SMS_DPGroupDistributionStatus` class doesn't define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of distribution points.

`ContentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of packages or applications distributed to this distribution point group.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique identifier for the distribution point group.

`MessageCategory` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Status message category.

`MessageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

See [SMS_StatusMessage Server WMI Class](../manage/sms_statusmessage-server-wmi-class).

`StatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time, in Universal Coordinated Time (UTC), when the status message was created.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).