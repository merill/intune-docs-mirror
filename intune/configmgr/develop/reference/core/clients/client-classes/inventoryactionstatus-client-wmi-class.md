---
layout: Conceptual
title: InventoryActionStatus Client WMI Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventoryactionstatus-client-wmi-class
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
description: The InventoryActionStatus class is a client Windows Management Instrumentation (WMI) class that defines the status of an inventory action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 43eaab82-ea8d-7582-5855-9148110e8f7c
document_version_independent_id: 94295fa2-6e7d-99b6-4fc3-a571f2e97e57
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/inventoryactionstatus-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/inventoryactionstatus-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/inventoryactionstatus-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f36ef350-fbc0-5025-525d-a69384489479
---

# InventoryActionStatus Client WMI Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `InventoryActionStatus` class is a client Windows Management Instrumentation (WMI) class that defines the status of an inventory action.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class InventoryActionStatus
{
      String InventoryActionID;
      DateTime LastCycleStartedDate;
      UInt32 LastMajorReportVersion;
      UInt32 LastMinorReportVersion;
      DateTime LastReportDate;
};
```

## Methods

The `InventoryActionStatus` class does not define any methods.

## Properties

`InventoryActionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The inventory action ID.

`LastCycleStartedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The time when the last inventory cycle started.

`LastMajorReportVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The major version of the last major report.

`LastMinorReportVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The minor version on the last report.

`LastReportDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time of the last report.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).