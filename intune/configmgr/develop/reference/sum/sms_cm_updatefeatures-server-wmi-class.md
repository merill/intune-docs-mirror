---
layout: Conceptual
title: SMS_CM_UpdateFeatures Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatefeatures-server-wmi-class
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
description: The  SMS_CM_UpdateFeatures Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents update feature extensions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d9e4a6a5-c98c-a9fe-917a-b4022ffbe469
document_version_independent_id: 04c9b59d-6398-5d32-91e3-b475e8519563
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatefeatures-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatefeatures-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatefeatures-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be638221-4791-0710-03ad-6014c75ad68a
---

# SMS_CM_UpdateFeatures Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdateFeatures` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents update feature extensions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdateFeatures : SMS_BaseClass
{
    DateTime DateReleased;
    String Description;
    String EULA;
    UInt32 Exposed;
    String FeatureGuid
    SInt32 FeatureType;
    SInt32 LocaleID;
    String MoreInfoLink;
    String Name;
    SInt32 Status;
};

```

## Methods

The following table lists the methods in the `SMS_CM_UpdateFeatures` class.

| Method | Description |
| --- | --- |
| [UpdateFeatureExposureStatus Method in Class SMS_CM_UpdateFeatures](updatefeatureexposurestatus-method-in-class-sms_cm_updatefeatures) | Updates the feature exposure status for an update feature extension. |

## Properties

`DateReleased` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The release date of the package, including the feature.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for the feature extension.

`EULA` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Microsoft Software License Terms for the feature extension.

`Exposed` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Bit value for exposing a feature.

`FeatureGuid` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

A unique identifier for a feature.

`FeatureType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Flag indicating the latest type of the feature. The default value is 1.

`LocaleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The locale ID for the localized data.

`MoreInfoLink` Data type: `String`

Access type: Read/Write

Qualifiers: none

Link to additional information about the feature extension.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the feature extension.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Flag indicating whether a feature will be exposed.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).