---
layout: Conceptual
title: SMS_ContentPackage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class
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
description: An SMS Provider server class that represents the content package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 760e458d-929d-f1de-589c-9ef7d3d7873b
document_version_independent_id: 728666a7-aa5f-9474-1468-a63422dd7f3f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 78445184-027d-5a1e-732a-d25d1f7a6dbc
---

# SMS_ContentPackage Class - Configuration Manager | Microsoft Learn

The `SMS_ContentPackage` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the content package.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ContentPackage : SMS_PackageBaseclass
{
    UInt32 ActionInProgress;
    String AlternateContentProviders;
    String Description;
    UInt8 ExtendedData[];
    UInt32 ExtendedDataSize;
    UInt32 ForcedDisconnectDelay;
    Boolean ForcedDisconnectEnabled;
    UInt32 ForcedDisconnectNumRetries;
    UInt8 Icon[];
    UInt32 IconSize;
    Boolean IgnoreAddressSchedule;
    UInt8 ISVData[];
    UInt32 ISVDataSize;
    String Language;
    DateTime LastRefreshTime;
    String LocalizedCategoryInstanceNames[];
    String Manufacturer;
    String MIFFilename;
    String MIFName;
    String MIFPublisher;
    String MIFVersion;
    String Name;
    UInt32 NumOfPrograms;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 PackageSize;
    UInt32 PackageType;
    UInt32 PkgFlags;
    UInt32 PkgSourceFlag;
    String PkgSourcePath;
    String PreferredAddressType;
    UInt32 Priority;
    Boolean RefreshPkgSourceFlag;
    SMS_ScheduleToken RefreshSchedule[];
    String SecuredScopeNames[];
    String SecurityKey;
    String SedoObjectVersion;
    String ShareName;
    UInt32 ShareType;
    DateTime SourceDate;
    String SourceSite;
    UInt32 SourceVersion;
    String StoredPkgPath;
    UInt32 StoredPkgVersion;
    String Version;
};
```

## Methods

The following table lists the methods in the `SMS_ContentPackage` class.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS_ContentPackage](addchangenotification-method-in-class-sms_contentpackage) | Adds a package change notification. |
| [AddContent Method in Class SMS_ContentPackage](addcontent-method-in-class-sms_contentpackage) | Adds a set of contents to this content package |
| [AddDistributionPointGroup Method in Class SMS_ContentPackage](adddistributionpointgroup-method-in-class-sms_contentpackage) | Adds a distribution point group for the content package. |
| [AddDistributionPoints Method in Class SMS_ContentPackage](adddistributionpoints-method-in-class-sms_contentpackage) | Adds the distribution points for the content package. |
| [Commit Method in Class SMS_ContentPackage](commit-method-in-class-sms_contentpackage) | Called when all the contents have been added to the content package to start package processing. |
| [RemoveContent Method in Class SMS_ContentPackage](removecontent-method-in-class-sms_contentpackage) | Removes the content for the given ContentID from the package. |
| [RefreshPkgSource Method in Class SMS_ContentPackage](refreshpkgsource-method-in-class-sms_contentpackage) | Causes a refresh of the package source. |
| [Unlock Method in Class SMS_ContentPackage](unlock-method-in-class-sms_contentpackage) | Sets the source site to the current site, unlocking the package. **Important:** This method is obsolete. |
| [SetSourceSite Method in Class SMS_ContentPackage](setsourcesite-method-in-class-sms_contentpackage) | Sets the code of the source site for the package. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: [large, lazy, resdll, resid]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ExtendedData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ExtendedDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectNumRetries` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`IgnoreAddressSchedule` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ISVData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ISVDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Language` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`LastRefreshTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Manufacturer` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`MIFFilename` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`MIFName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`MIFPublisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`MIFVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`NumOfPrograms` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The security type of the content.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PackageSize` Data type: `UInt32`

Access type: Read

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PkgFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PkgSourceFlag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PkgSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`PreferredAddressType` Data type: `String`

Access type: Read/Write

Qualifiers: [stringenumeration]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type: Read/Write

Qualifiers: [lazy, max]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

The security key of the content. Content may security by app or package.

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ShareName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`ShareType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Specifies whether the package uses the common package share on the distribution point or a custom share.

`SourceDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`SourceVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`StoredPkgPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`StoredPkgVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](sms_packagebaseclass-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).