---
layout: Conceptual
title: SMS_BoundaryGroupSiteSystems Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupsitesystems-server-wmi-class
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
description: The SMS_BoundaryGroupSiteSystems WMI class represents site systems that serve computers within the boundary group.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 62a2cd16-d1af-a857-c773-719fc3aa5538
document_version_independent_id: ea595a85-742e-6928-b900-8926fb00b7e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupsitesystems-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_boundarygroupsitesystems-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupsitesystems-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4d2b936d-313c-1d78-f2c9-f1a71c9f1722
---

# SMS_BoundaryGroupSiteSystems Class - Configuration Manager | Microsoft Learn

The `SMS_BoundaryGroupSiteSystems` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents site systems that serve computers within the boundary group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupSiteSystems : SMS_BaseClass
{
    UInt32 Flags;
    UInt32 GroupID;
    String ServerNALPath;
    String SiteCode;
};
```

## Methods

The `SMS_BoundaryGroupSiteSystems` class does not define any methods.

## Properties

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Specifies the connection type of the boundary. Possible values are:

| Value | Description |
| --- | --- |
| 0 | FAST |
| 1 | SLOW |

Note

This parameter is no longer used for distribution points.

`GroupID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Unique identifier of the boundary group.

`ServerNALPath` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

NAL path of site system servicing machines within the boundary.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read, sizelimit("3")]

Site code of the role.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).