---
layout: Conceptual
title: SMS_DistributionJob Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionjob-server-wmi-class
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
description: An SMS Provider server class that represents a distribution point job.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a5e2d19c-1522-8bd0-1775-2a598160c8f6
document_version_independent_id: 66f0fc8c-de17-e126-15a9-654eaffb405a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_distributionjob-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_distributionjob-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_distributionjob-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 8bf7013c-211c-e44e-8e92-1246fef86c31
---

# SMS_DistributionJob Class - Configuration Manager | Microsoft Learn

The `SMS_DistributionJob` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a distribution point job.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionJob : SMS_BaseClass
{
    UInt32 Action;
    Datetime CreationTime;
    UInt32 DPID;
    UInt32 DynamicOrder;
    UInt64 JobID;
    Datetime LastUpdateTime;
    String NALPath;
    UInt32 PackageVersion;
    String PkgID;
    UInt32 RemainingSize;
    UInt32 ReStartTime;
    UInt32 RetryCount;;
    Datetime StartTime;
    UInt32 State;
    UInt64 TotalSize;
};
```

## Methods

The `SMS_DistributionJob` class does not define any methods.

## Properties

`Action` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Current job action. Possible values are:

| Value | Job action |
| --- | --- |
| 1 | DISTSRC\_ACTION\_UPDATE |
| 2 | DISTSRC\_ACTION\_ADD |
| 5 | DISTSRC\_ACTION\_CANCEL |

`CreationTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Job creation time.

`DPID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Distribution point identifier.

`DynamicOrder` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Dynamic order for the job.

`JobID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read, key]

Job identifier.

`LastUpdateTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Last update time of the job.

`NALPath` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Distribution point NAL path.

`PackageVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Package version.

`PkgID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Package identifier.

`RemainingSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Remaining size of the distribution job.

`ReStartTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Job restart time.

`RetryCount` Data type: `UIn32`

Access type: Read-only

Qualifiers: [read]

Retry count.

`StartTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Job start time.

`State` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Current job state. Possible values are:

`TotalSize` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

Date of the last status update.

| Value | Job state |
| --- | --- |
| 0 | DISTSRC\_STATE\_PENDING |
| 1 | DISTSRC\_STATE\_READY |
| 2 | DISTSRC\_STATE\_STARTED |
| 3 | DISTSRC\_STATE\_INPROGRESS |
| 4 | DISTSRC\_STATE\_PENDING\_RESTART |
| 5 | DISTSRC\_STATE\_COMPLETE |
| 6 | DISTSRC\_STATE\_FAILED |
| 7 | DISTSRC\_STATE\_CANCELLED |
| 8 | DISTSRC\_STATE\_SUSPENDED |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).