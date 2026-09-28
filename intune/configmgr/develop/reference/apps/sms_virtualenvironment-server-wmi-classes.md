---
layout: Conceptual
title: SMS_VirtualEnvironment Classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_virtualenvironment-server-wmi-classes
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
description: Learn how to track the history of a request each time a request is updated using SMS_VirtualEnvironment in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 03d06e1e-5e99-62fa-9974-312b120d04aa
document_version_independent_id: f31329a3-d907-2ad2-9fbe-0a0ff11092f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_virtualenvironment-server-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_virtualenvironment-server-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_virtualenvironment-server-wmi-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b1b9786a-04d3-1aa4-f3e9-99a1c73863e2
---

# SMS_VirtualEnvironment Classes - Configuration Manager | Microsoft Learn

The `SMS_VirtualEnvironment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UserApplicationRequestHistoryItem :
{
    boolean IsReadOnly;;
    SMS_CI_LocalizedProperties LocalizedInformation[];
    uint32 NumReferringApplications;
    uint32 NumReferringDeploymentTypes;
    uint32 ReferringDeploymentTypes[];
};
```

## Methods

The `SMS_UserApplicationRequestHistoryItem` class does not define any methods.

## Properties

`IsReadOnly` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Flag to indicate the virtual environment is read-only.

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: [lazy]

Localized information.

`NumReferringApplications` Data type: `UInt32`

Access type: Read

Qualifiers: [read, not\_null]

The number of referring applications.

`NumReferringDeploymentTypes` Data type: `UInt32`

Access type: Read

Qualifiers: [read, not\_null]

The number of referring deployment types.

`ReferringDeploymentTypes` Data type: `UInt32` Array

Access type: Read/Write

Qualifiers: [lazy]

A list of CI\_IDs of the referring deployment types.

## Remarks

## Requirements

Each time a request is updated, an instance of this class is created to track the history of the request.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).