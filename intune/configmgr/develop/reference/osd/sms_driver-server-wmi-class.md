---
layout: Conceptual
title: SMS_Driver Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class
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
description: In Configuration Manager, the SMS_Driver Windows Management Instrumentation class is an SMS Provider server class that represents device drivers in the driver catalog that can be installed as part of a task sequence in an operating system deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3c18b95a-aed4-52be-993b-930d301f7b99
document_version_independent_id: 546bcd34-32ec-ea4f-d7b1-cd33971d2d51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_driver-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 530d1f7b-2ee5-d826-da49-539587f3b12f
---

# SMS_Driver Class - Configuration Manager | Microsoft Learn

The `SMS_Driver` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents device drivers, in the driver catalog, that can be installed as part of a task sequence in an operating system deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Driver : SMS_ConfigurationItemBaseClass
{
      String ApplicabilityCondition;
      String CategoryInstance_UniqueIDs[];
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIType_ID;
      UInt32 CIVersion;
      UInt64 ConfigurationFlags;
      String ContentSourcePath;
      String CreatedBy;
      DateTime DateCreated;
      DateTime DateLastModified;
      Boolean DriverBootCritical;
      String DriverClass;
      DateTime DriverDate;
      String DriverINFFile;
      String DriverProvider;
      Boolean DriverSigned;
      String DriverSigner;
      String DriverType;
      String DriverVersion;
      DateTime EffectiveDate;
      UInt32 EULAAccepted;
      Boolean EULAExists;
      DateTime EULASignoffDate;
      String EULASignoffUser;
      UInt32 ExecutionContext;
      Boolean IsBundle;
      Boolean IsDigest;
      Boolean IsEnabled;
      Boolean IsExpired;
      Boolean IsHidden;
      Boolean IsLatest;
      Boolean IsQuarantined;
      Boolean IsSuperseded;
      Boolean IsUserDefined;
      String LastModifiedBy;
      String LocalizedCategoryInstanceNames[];
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

The following table shows the methods in `SMS_Driver`.

| Method | Description |
| --- | --- |
| [CreateFromINF Method in Class SMS_Driver](createfrominf-method-in-class-sms_driver) | Creates an `SMS_Driver` object based on information from the specified source path and INF file. |
| [CreateFromINFs Method in Class SMS_Driver](createfrominfs-method-in-class-sms_driver) | Creates `SMS_Driver` objects based on information from the specified source path and one or more INF files. |
| [CreateFromOEM Method in Class SMS_Driver](createfromoem-method-in-class-sms_driver) | Creates a set of `SMS_Driver` objects referenced by the specified Txtsetup.oem file. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers:[unique, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

For this class, the type ID is Driver (6).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContentSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

The location of the driver files. When a driver is added to a driver package or a boot image the SMS Provider copies files from this location. The path must be a Universal Naming Convention (UNC) path accessible by the SMS Provider, for example, \\smsserver\drivers\microsoft\vmscsi, as the path for INF files.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`DriverBootCritical` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the driver is boot-critical. A mass storage driver imported from a txtsetup.oem file that needs to be installed before booting into a pre-Windows Vista operating system.

`DriverClass` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The class of device that the driver supports (such as Net or Display) as reported by the driver's INF file.

`DriverDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the driver was written as reported by the INF file.

`DriverINFFile` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Relative path and file name of the driver INF file, relative to `ContentSourcePath`.

`DriverProvider` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the company or author of the driver file as reported in the INF file. This property does not necessarily reflect the device manufacturer.

`DriverSigned` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the driver source file is digitally signed by a recognized authority. For example, the Windows Hardware Quality Lab.

`DriverSigner` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the digital signer if the driver source file is signed.

`DriverType` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The type of driver. Currently the only valid value for this is INF.

`DriverVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Version number of the driver, as specified by the driver provider.

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: [lazy]

Not used.

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read/Write

Qualifiers: [lazy]

Language-specific localized information about the driver:

- String DisplayName
- String Description
- String InformativeURL
- UInt32 LocaleID

    This property is used to change the display name and description for a driver that supports multiple languages.

    `LocalizedInformativeURL` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `LocalizedPropertyLocaleID` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `ModelName` Data type: `String`

    Access type: Read/Write

    Qualifiers: [unique, not\_null]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `ModelID` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `PermittedUses` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `PlatformType` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

    `PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

    `SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

    Access type: Read/Write

    Qualifiers: [lazy]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `SDMPackageVersion` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [not\_null]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `SDMPackageXML` Data type: `String`

    Access type: Read/Write

    Qualifiers: [lazy]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

    `SecuredScopeNames` Data type: `String Array`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

    `SedoObjectVersion` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

    `SourceSite` Data type: `String`

    Access type: Read/Write

    Qualifiers: [SizeLimit("3")]

    See [SMS_ConfigurationItemBaseClass Server WMI Class](../compliance/sms_configurationitembaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Configuration Manager uses a driver catalog to manage the different computers, devices, and associated Windows device drivers that it supports. For more information, see [Manage drivers](../../../osd/get-started/manage-drivers).

    You can create an `SMS_Driver` object by using the [CreateFromINF Method in Class SMS_Driver](createfrominf-method-in-class-sms_driver) and [CreateFromOEM Method in Class SMS_Driver](createfromoem-method-in-class-sms_driver) methods. You use [CreateFromINF Method in Class SMS_Driver](createfrominf-method-in-class-sms_driver) to create an `SMS_Driver` Object from a Windows driver INF file. For more information see, How to Import a Windows Driver Described by an INF File into Configuration Manager. You use [CreateFromOEM Method in Class SMS_Driver](createfromoem-method-in-class-sms_driver) to create an `SMS_Driver` object from a Txtsetup.oem file.

    Drivers share many of the abstract qualities of configuration items but you cannot use drivers like configuration items. For example, they cannot be assigned to baselines.

    Drivers can be arranged into categories by adding the relevant category identifier to the `SMS_Driver Server WMI Class``CategoryInstance_UniqueIDs` array property. For more information, see How to Add a Category to a Windows Driver.

    When you use the Configuration Manager server WMI classes in your application or script, remember that each driver must be added to at least one driver package ([UPDATED: SMS_DriverPackage Server WMI Class](sms_driverpackage-server-wmi-class)) before it can be installed on a client. For more information, see How to Create a Driver Package for a Windows Driver in Configuration Manager. Mass storage drivers may also be added to a boot image package, represented by [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class). How to add a Windows Driver to a Configuration Manager Boot Image Package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).