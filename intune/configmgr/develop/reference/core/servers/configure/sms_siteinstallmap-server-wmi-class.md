---
layout: Conceptual
title: SMS_SiteInstallMap Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class
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
description: Learn how to represent the site install map, which describes the layout of all installed features in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e36a18c5-1dbd-d641-e96f-21e08de81549
document_version_independent_id: 58330947-1813-f135-bf78-3a292b88e284
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0a108b37-ab0e-9e03-3038-e325541ed552
---

# SMS_SiteInstallMap Class - Configuration Manager | Microsoft Learn

The `SMS_SiteInstallMap` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the site install map, which describes the layout of all installed features.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteInstallMap : SMS_BaseClass
{
     String BuildNumber;
     UInt32 FileType;
     String FormatVersion;
     String IMapData;
};
```

## Methods

The following table lists the method in `SMS_SiteInstallMap`.

| Method | Description |
| --- | --- |
| [Refresh Method in Class SMS_SiteInstallMap](refresh-method-in-class-sms_siteinstallmap) | Reloads the install map from the database, which repopulates the classes. |

## Properties

`BuildNumber` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Configuration Manager build number.

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Reserved. Initialized with a value of 1.

`FormatVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Format version of the install map.

`IMapData` Data type: `String`

Access type: Read-only

Qualifiers: [large, lazy]

Install map data in text format.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Use classes derived from [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class) to view the install map.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).