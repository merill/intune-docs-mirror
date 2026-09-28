---
layout: Conceptual
title: SMS_CM_UpdatePackageFeatures Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackagefeatures-server-wmi-class
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
description: Learn how to use the SMS_CM_UpdatePackageFeatures class in Configuration Manager to update feature extensions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 90d79d31-cd30-3333-9b66-7eef133361c3
document_version_independent_id: 7f5ae428-33ef-d994-cae5-4083fc7fd6eb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatepackagefeatures-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatepackagefeatures-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatepackagefeatures-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3ec61997-3469-0cb6-baa5-cf1afba15ee8
---

# SMS_CM_UpdatePackageFeatures Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdatePackageFeatures` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents update feature extensions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackageFeatures : SMS_BaseClass
{
    String Description;
    String EULA;
    UInt32 Exposed;
    String FeatureGuid;
    SInt32 FeatureType;
    SInt32 Flag;
    SInt32 LocaleID;
    String MoreInfoLink;
    String Name;
    String PackageGuid;
    SInt32 Status;
 };

```

## Methods

The following table lists the methods in the `SMS_CM_UpdatePackageFeatures` class.

| Method | Description |
| --- | --- |
| [UpdateFeatureExposureStatus Method in Class SMS_CM_UpdatePackageFeatures](updatefeatureexposurestatus-method-in-class-sms_cm_updatepackagefeatures) | Updates the feature exposure status for an update package feature extension. |

## Properties

`Description` Data type: `String`

Access type: Read

Qualifiers: none

Description for the feature extension.

`EULA` Data type: `String`

Access type: Read

Qualifiers: [lazy]

Microsoft Software License Terms for the feature extension.

`Exposed` Data type: `UInt32`

Access type: Read

Qualifiers: none

Bit value for exposing a feature.

`FeatureGuid` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

A unique identifier for a feature.

`FeatureType` Data type: `SInt32`

Access type: Read

Qualifiers: none

Type of the feature in the package.

`Flag` Data type: `SInt32`

Access type: Read

Qualifiers: none

Flag indicating the latest type of the feature.

`LocaleID` Data type: `SInt32`

Access type: Read

Qualifiers: none

The locale ID for the localized data.

`MoreInfoLink` Data type: `String`

Access type: Read

Qualifiers: none

Link to additional information about the feature extension.

`Name` Data type: `String`

Access type: Read

Qualifiers: none

Name of the feature extension.

`PackageGuid` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

A unique identifier for the feature.

`Status` Data type: `SInt32`

Access type: Read

Qualifiers: none

Flag indicating whether a feature will be exposed.

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