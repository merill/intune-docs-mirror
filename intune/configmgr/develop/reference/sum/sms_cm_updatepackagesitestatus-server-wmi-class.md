---
layout: Conceptual
title: SMS_CM_UpdatePackageSiteStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackagesitestatus-server-wmi-class
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
description: The  `SMS_CM_UpdatePackageSiteStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to get the update package installation status per site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2a9313d7-175f-5a43-f432-32ab75710db9
document_version_independent_id: 2a853e14-34f8-52b5-0805-b43923a1301c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatepackagesitestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatepackagesitestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatepackagesitestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 033d0eb0-f48d-a364-4d53-07a643472d33
---

# SMS_CM_UpdatePackageSiteStatus Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdatePackageSiteStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to get the update package installation status per site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackageSiteStatus : SMS_BaseClass
{
    DateTime LastUpdateTime;
    String Name;
    String PackageGuid;
    SInt32 PrereqFlag;
    String SiteCode;
    String SiteName;
    SInt32 SiteNumber;
    String SiteServerName;
    Sint32 SiteType;
    Sint32 State;
};

```

## Methods

The following table lists the methods in the `SMS_CM_UpdatePackageSiteStatus` class.

| Method | Description |
| --- | --- |
| [UpdatePackageSiteState Method in Class SMS_CM_UpdatePackageSiteStatus](updatepackagesitestate-method-in-class-sms_cm_updatepackagesitestatus) | Updates the package installation state of the site. |

## Properties

`LastUpdateTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: none

The date and time that the state was last updated.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the update package.

`PackageGuid` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The unique identifier of the package.

`PrereqFlag` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Prerequisite flag. Possible values are: bits:

| Value | Description |
| --- | --- |
| 0x1 | Prereq only |
| 0x2 | CONTINUE\_ON\_PREREQ\_WARNING |

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The site code.

`SiteName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the site.

`SiteNumber` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The unique identifier of the site.

`SiteServerName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The site server name.

`SiteType` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The site type.

`State` Data type: `SInt32`

Access type: Read-only

Qualifiers: none

The state of the installation.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).