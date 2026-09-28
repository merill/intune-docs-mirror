---
layout: Conceptual
title: SMS_ConfigurationItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class
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
description: The SMS_ConfigurationItem Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a7737da3-dacf-1430-e074-d7c3d432c618
document_version_independent_id: d17157aa-d0e1-644f-96ee-36e7846d9cb8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b8352f43-c486-f67c-d77b-ce30d4663a3f
---

# SMS_ConfigurationItem Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigurationItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItem : SMS_ConfigurationItemBaseClass
{
      String ApplicabilityCondition;
      String CategoryInstance_UniqueIDs;[]
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIType_ID;
      UInt32 CIVersion;
      UInt64 ConfigurationFlags;
      String CreatedBy;
      DateTime DateCreated;
      DateTime DateLastModified;
      DateTime EffectiveDate;
      UInt32 EULAAccepted;
      Boolean EULAExists;
      DateTime EULASignoffDate;
      String EULASignoffUser;
      UInt32 ExecutionContext;
      Boolean InUse;
      Boolean IsBroken;
      Boolean IsBundle;
      Boolean IsChild;
      Boolean IsDigest;
      Boolean IsEnabled;
      Boolean IsExpired;
      Boolean IsHidden;
      Boolean IsLatest;
      Boolean IsQuarantined;
      Boolean IsSuperseded;
      Boolean IsUserDefined;
      String LastModifiedBy;
      String LocalizedCategoryInstanceNames;[]
      String LocalizedDescription;
      String LocalizedDisplayName;
      SMS_CI_LocalizedEulas LocalizedEulas[];
      SMS_CI_LocalizedProperties LocalizedInformation[];
      String LocalizedInformativeURL;
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ModelID;
      String ModelName;
      UInt32 PermittedUses;
      String PlatformCategoryInstance_UniqueIDs[];
      UInt32 PlatformType;
      SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
      UInt32 SDMPackageVersion;
      String SDMPackageXML;
      String SecuredScopeNames[];
      String SedoObjectVersion;
      String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_ConfigurationItem` class.

| Method | Description |
| --- | --- |
| [AcceptEULA Method in Class SMS_ConfigurationItem](accepteula-method-in-class-sms_configurationitem) | Accepts or declines the Microsoft Software License Terms of a configuration item. |
| [GetEULA Method in Class SMS_ConfigurationItem](geteula-method-in-class-sms_configurationitem) | Gets the localized Microsoft Software License Terms content of the configuration item. |
| [GetSDMDefinition Method in Class SMS_ConfigurationItem](getsdmdefinition-method-in-class-sms_configurationitem) | Retrieves the System Definition Model (SDM) definition of the configuration item in XML format. |
| [SetEnforcement Method in Class SMS_ConfigurationItem](setenforcement-method-in-class-sms_configurationitem) | Sets the enforcement and the enforcement date for a configuration item. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers:[unique, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

For this class, the type ID is OtherConfigurationItem (7).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`InUse` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

[SMS_ConfigurationBaselineInfo Server WMI Class](sms_configurationbaselineinfo-server-wmi-class)

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the configuration item is broken.

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsChild` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this configuration item is a child of other configuration item.

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: `Read/Write`

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: [lazy]

An array of localized Microsoft Software License Terms for the configuration item.

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: [lazy]

A list of language-specific localized information about the configuration item:

- `String` DisplayName
- `String` Description
- `String` InformativeURL
- `UInt32` LocaleID

    `LocalizedInformativeURL` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `LocalizedPropertyLocaleID` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `ModelID` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `ModelName` Data type: `String`

    Access type: Read-only

    Qualifiers: [unique, not\_null]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `PermittedUses` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

    Access type: Read/Write

    Qualifiers: none

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `PlatformType` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [bitmap, bitvalues, read]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

    Access type: Read/Write

    Qualifiers: [lazy]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SDMPackageVersion` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SDMPackageXML` Data type: `String`

    Access type: Read/Write

    Qualifiers: [lazy]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SecuredScopeNames` Data type: `String Array`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SedoObjectVersion` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

    `SourceSite` Data type: `String`

    Access type: Read-only

    Qualifiers: [SizeLimit("3")]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class by creating an object and getting and setting the properties as required for the particular configuration.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).