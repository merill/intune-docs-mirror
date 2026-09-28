---
layout: Conceptual
title: SMS_CM_UpdatePackDetailedPrereqMonitoring Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedprereqmonitoring-server-wmi-class
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
description: In Configuration Manager, the SMS_CM_UpdatePackDetailedPrereqMonitoring WMI class is an SMS Provider server class that is used to get detailed update package prerequisite status per site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 63392e69-c635-9239-53ec-55bb102fd73c
document_version_independent_id: 300eeb85-8625-b914-0fa5-8400a9707d4e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedprereqmonitoring-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatepackdetailedprereqmonitoring-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedprereqmonitoring-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1bdf5772-8198-f9ea-51a1-167a75121849
---

# SMS_CM_UpdatePackDetailedPrereqMonitoring Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdatePackDetailedPrereqMonitoring` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to get detailed update package prerequisite status per site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackDetailedPrereqMonitoring: SMS_BaseClass  
{  
    SInt32 Applicable;  
    String Description;  
    SInt32 IsComplete;  
    DateTime MessageTime;  
    SInt32 OrderId;  
    String PackageGuid;  
    SInt32 Progress;  
    String SiteCode;  
    SInt32 SiteInstallID;  
    SInt32 SiteNumber;  
    SInt32 SiteType;  
    SInt32 StageId;  
    String SubStageName;  
};  

```

## Methods

The `SMS_CM_UpdatePackDetailedPrereqMonitoring` class does not define any methods.

## Properties

`Applicable` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Indicates whether the `SubStage` is applicable.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: [read]

A description of the `SubStage`.

`IsComplete` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Indicates whether the `SubStage` has completed.

`MessageTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time that the message was created.

`OrderId` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The order in which the `SubStage`s are listed in the user interface.

`PackageGuid` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, not\_null]

Unique identifier of the update package.

`Progress` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The progress of the `SubStage`.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, not\_null]

Unique identifier of the site.

`SiteInstallID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [none]

The number of installation retires.

`SiteNumber` Data type: `Sint32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

Unique identifier of the site.

`SiteType` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The type of site to which the `SubStage` applies.

`StageId` Data type: `Sint32`

Access type: Read-only

Qualifiers: [read]

The top-level stage with which the `SubStage` is associated.

`SubStageName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the SubStage.

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