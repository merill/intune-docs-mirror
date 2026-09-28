---
layout: Conceptual
title: SMS_SoftwareUpdateSource Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class
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
description: Lists all software update sources available on the site, for use in synchronizing metadata during a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 09196246-5b83-5afa-9ab3-11fe9632707a
document_version_independent_id: e214b2d4-da54-cd00-d35c-bc329ac9c434
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 968bf10e-502d-dc0c-35e8-e4d418d45408
---

# SMS_SoftwareUpdateSource Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareUpdateSource` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists all software update sources available on the site, for use in synchronizing metadata during a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareUpdateSource : SMS_BaseClass  
{  
      String ApplicabilityCondition;  
      DateTime DateCreated;  
      DateTime DateModified;  
      Boolean IsExpired;  
      String PublicKeys;  
      String ScanMethod;  
      String ScanMethodParameters;  
      String ScannerToolPkgID;  
      UInt32 ScanType;  
      UInt32 SourceContentType;  
      String SourceSite;  
      String UpdateSourceDescription;  
      UInt32 UpdateSourceID;  
      String UpdateSourceName;  
      String UpdateSourceUniqueID;  
      String UpdateSourceVersion;  
      String UpdateType;  
};  
```

## Methods

The `SMS_SoftwareUpdateSource` class does not define any methods.

Note

The `ResendObjectToAllSites Method in Class SMS_SoftwareUpdateSource` has been deprecated in Configuration Manager.

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: None

Condition that the client evaluates before evaluating a software update. If the condition does not exist, the update is not evaluated.

`DateCreated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the update source was created.

`DateModified` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the update source was last modified.

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if the update source is no longer active. The default value is `false`.

`PublicKeys` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Public keys with which all the associated binaries are signed.

`ScanMethod` Data type: `String`

Access type: Read/Write

Qualifiers: None

Scan method for the update source.

`ScanMethodParameters` Data type: `String`

Access type: Read/Write

Qualifiers: None

Scan method parameters.

`ScannerToolPkgID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

ID of the scanner tool package associated with the update source.

`ScanType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Type of scan to use for the source. Possible values are:

- WSUS
- Offline source

    `SourceContentType` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Type of content distributed by the update source.

    `SourceSite` Data type: `String`

    Access type: Read/Write

    Qualifiers: [not\_null]

    Site code for the update source site.

    `UpdateSourceDescription` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Description of the update source.

    `UpdateSourceID` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [key, not\_null]

    The unique ID of the software update source. This ID is unique only for the site.

    `UpdateSourceName` Data type: `String`

    Access type: Read/Write

    Qualifiers: [not\_null]

    Name of the update source.

    `UpdateSourceUniqueID` Data type: `String`

    Access type: Read/Write

    Qualifiers: [not\_null]

    The unique ID for the update source. This ID is unique across sites.

    `UpdateSourceVersion` Data type: `String`

    Access type: Read/Write

    Qualifiers: [not\_null]

    Version of the update source.

    `UpdateType` Data type: `String`

    Access type: Read/Write

    Qualifiers: [not\_null]

    Type of the update source.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Your application uses this class to set or modify the source of a software update so that metadata is properly synchronized during update deployment. Currently, the supported sources for software updates are Windows Server Update Services (WSUS) and ITMU/Offline Catalog.

To use this class, the application creates an `SMS_SoftwareUpdateSource` object and sets the properties as required for the particular software update and the source.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).