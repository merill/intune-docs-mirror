---
layout: Conceptual
title: SMS_CM_UpdatePackDetailedSiteStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedsitestatus-server-wmi-class
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
description: In Configuration Manager, the  SMS_CM_UpdatePackDetailedSiteStatus WMI class is an SMS Provider server class that is used to get detailed update package installation status per site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 107d848b-6098-bb8b-c256-fc4b8521d28e
document_version_independent_id: c8dd08c9-7b36-1e35-d929-179ef57cdf33
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedsitestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatepackdetailedsitestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedsitestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c68b9e84-5218-09c8-af97-2791d2008f1b
---

# SMS_CM_UpdatePackDetailedSiteStatus Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdatePackDetailedSiteStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to get detailed update package installation status per site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackDetailedSiteStatus : SMS_BaseClass  
{  
    DateTime MessageTime;  
    String PackageGuid;  
    String SiteCode;  
    SInt32 SiteInstallID;  
    SInt32 SiteNumber;  
    String StatusDescription;  
    SInt32 StatusID;  
    String StatusName;  
    SInt32 SubStatusID;  
};  

```

## Methods

The `SMS_CM_UpdatePackDetailedSiteStatus` class does not define any methods.

## Properties

`MessageTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time that the message was created.

`PackageGuid` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Unique identifier of the update package.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, not\_null]

Unique identifier of the site.

`SiteInstallID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The number of installation retires.

`SiteNumber` Data type: `Sint32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

Unique identifier of the site.

`StatusDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the status.

`StatusID` Data type: `Sint32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The status ID.

`StatusName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the status.

`SubStatusID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The ID of the `SubStatus`.

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