---
layout: Conceptual
title: SMS_BoundaryGroupMembers Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupmembers-server-wmi-class
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
description: Learn how the SMS_BoundaryGroupMembers Windows Management Instrumentation (WMI) class is an SMS Provider server class that represents boundary group members.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0bd66abb-5e01-37ca-5dbd-1dd96ac05234
document_version_independent_id: 7b4c8534-9358-3d58-cc5d-4aac666fc5c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupmembers-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_boundarygroupmembers-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupmembers-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ac46e1ad-2130-27e5-f73d-9afe776fbf5c
---

# SMS_BoundaryGroupMembers Class - Configuration Manager | Microsoft Learn

The `SMS_BoundaryGroupMembers` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents boundary group members.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupMembers : SMS_BaseClass
{
    UInt32 BoundaryID;
    UInt32 GroupID;
};
```

## Methods

The `SMS_BoundaryGroupMembers` class does not define any methods.

## Properties

`BoundaryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique identifier of the boundary.

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique identifier for the boundary group.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).