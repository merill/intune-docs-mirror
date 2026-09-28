---
layout: Conceptual
title: SMS_BootImagePackage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class
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
description: The SMS_BootImagePackage WMI class is an SMS Provider server class, in Configuration Manager, that serves as the unit of distribution for boot image source files.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2db8e618-449f-9810-8041-70368d243c03
document_version_independent_id: fdb10330-98d0-0c07-3e23-c96584101c36
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 74327488-c61a-a41f-567d-74c426215d69
---

# SMS_BootImagePackage Class - Configuration Manager | Microsoft Learn

The `SMS_BootImagePackage` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as the unit of distribution for boot image source files that are used to start a computer with Windows Pre-Installation Environment (PE) 2.0 and allow operating system deployment task sequence actions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BootImagePackage : SMS_PackageBaseclass
{
      UInt32 ActionInProgress;
      String AlternateContentProviders;
      String Architecture;
      String BackgroundBitmapPath;
      String ContextID;
      Boolean DefaultImage;
      String Description;
      Boolean EnableLabShell;
      UInt8 ExtendedData[];
      UInt32 ExtendedDataSize;
      UInt32 ForcedDisconnectDelay;
      Boolean ForcedDisconnectEnabled;
      UInt32 ForcedDisconnectNumRetries;
      UInt8 Icon[];
      UInt32 IconSize;
      Boolean IgnoreAddressSchedule;
      String ImageDiskLayout;
      UInt32 ImageIndex;
      String ImageOSVersion;
      String ImagePath;
      String ImageProperty;
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
      UInt32 OptionalComponents[];
      String PackageID;
      UInt32 PackageSize;
      UInt32 PackageType;
      UInt32 PkgFlags;
      UInt32 PkgSourceFlag;
      String PkgSourcePath;
      String PreExecCommandLine;
      String PreExecSourceDirectory;
      String PreferredAddressType;
      UInt32 Priority;
      SMS_Driver_Details ReferencedDrivers[];
      Boolean RefreshPkgSourceFlag;
      SMS_ScheduleToken RefreshSchedule[];
      UInt32 ScratchSpace;
      String SecuredScopeNames[];
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

The following table shows the methods in `SMS_BootImagePackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS_BootImagePackage](addchangenotification-method-in-class-sms_bootimagepackage) | Adds a boot image package change notification. |
| [AddDistributionPoints Method in Class SMS_BootImagePackage](adddistributionpoints-method-in-class-sms_bootimagepackage) | Adds the distribution points for the package. |
| [DeleteContextID Method in Class SMS_BootImagePackage](deletecontextid-method-in-class-sms_bootimagepackage) | Deletes the status queue that is associated with the specified context ID for the boot image package. |
| [ExportDefaultBootImage Method in Class SMS_BootImagePackage](exportdefaultbootimage-method-in-class-sms_bootimagepackage) | Finalizes and exports a boot image from a Windows Assessment and Deployment Kit installation source to a specified location. |
| [GetImageProperties Method in Class SMS_BootImagePackage](getimageproperties-method-in-class-sms_bootimagepackage) | Reads all image properties from the specified source .wim file to an XML string. |
| [QueryOSDBinaryInjectionStatus Method in Class SMS_BootImagePackage](queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage) | Queries the current status of the injection of operating system deployment binaries. |
| [RefreshPkgSource Method in Class SMS_BootImagePackage](refreshpkgsource-method-in-class-sms_bootimagepackage) | Refreshes the package source at all distribution points, when the package properties have not changed. |
| [ReloadImageProperties Method in Class SMS_BootImagePackage](reloadimageproperties-method-in-class-sms_bootimagepackage) | Reloads image properties from the source .wim file and updates the database. |
| [SetSourceSite Method in Class SMS_BootImagePackage](setsourcesite-method-in-class-sms_bootimagepackage) | Sets the code of the source site for the boot image package. |
| [Unlock Method in Class SMS_BootImagePackage](unlock-method-in-class-sms_bootimagepackage) | Sets the source site to the current site, unlocking the boot image package. |
| [UpdateDefaultImage Method in Class SMS_BootImagePackage](updatedefaultimage-method-in-class-sms_bootimagepackage) | Creates a copy of the WIM image pointed to by the ImagePath property and injects it with OSD files for boot image deployment. |
| [UpdateImage Method in Class SMS_BootImagePackage](updateimage-method-in-class-sms_bootimagepackage) | Creates a copy of the image for the boot image package and updates the image with files for boot image deployment. |
| [UpdateOptionalComponents Method in Class SMS_BootImagePackage](updateoptionalcomponents-method-in-class-sms_bootimagepackage) | Updates all specified optional components to the boot image. |

## Properties

`Architecture` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Architecture of the boot image. The following values are the possible values. The default value is "".

| Value | Architecture |
| --- | --- |
| x86 | I386 32-bit microprocessor |
| ia64 | Itanium 64-bit microprocessor |
| x64 | X86-64 64-bit microprocessor |

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`BackgroundBitmapPath` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Universal Naming Convention (UNC) path of the WinPE background bitmap. Your application can set this property to use a custom bitmap by supplying the path to the custom bitmap files.

`ContextID` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

A context ID that can be queried for the status of injecting operating system deployment binaries. The injection operation takes quite a while, and your application can use this property for periodic status. The default value is "".

`DefaultImage` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if this is a default boot image. The default value is `false`.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`EnableLabShell` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if command line support is enabled. The default value is `false`.

`ExtendedData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ExtendedDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectNumRetries` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`IgnoreAddressSchedule` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ImageDiskLayout` Data type: `String`

Access type: Read-only

Qualifiers: [lazy, read]

An XML string of disk layout information for the source image, represented by a .wim file (WIM format). The default value is "".

`ImageIndex` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

Not used for a boot image.

`ImageOSVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Operating system version for the default image in the boot WIM file.

`ImagePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Original image source path. Configuration Manager uses this path internally when the administrator imports an image. When the image is imported, Configuration Manager injects it with operating system deployment binaries.

`ImageProperty` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

An XML string holding metadata of the source .wim file, for example, the version. The default value is "".

`ISVData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ISVDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Language` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`LastRefreshTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Manufacturer` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFFilename` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFPublisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`NumOfPrograms` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`OptionalComponents` Data type: `UInt32` Array

Access type: Read/Write

Qualifiers: [lazy]

A list of identifiers of optional components that will be enabled in WinPE. Possible values are:

| Identifier | Component |
| --- | --- |
| 1 | WinPE-DismCmdlets |
| 2 | WinPE-Dot3Svc |
| 3 | WinPE-EnhancedStorage |
| 4 | WinPE-FMAPI |
| 5 | WinPE-FontSupport-JA-JP |
| 6 | WinPE-FontSupport-KO-KR |
| 7 | WinPE-FontSupport-ZH-CN |
| 8 | WinPE-FontSupport-ZH-HK |
| 9 | WinPE-FontSupport-ZH-TW |
| 10 | WinPE-HTA |
| 11 | WinPE-StorageWMI |
| 12 | WinPE-LegacySetup |
| 13 | WinPE-MDAC |
| 14 | WinPE-NetFx4 |
| 15 | WinPE-PowerShell3 |
| 16 | WinPE-PPPoE |
| 17 | WinPE-RNDIS |
| 18 | WinPE-Scripting |
| 19 | WinPE-SecureStartup |
| 20 | WinPE-Setup |
| 21 | WinPE-Setup-Client |
| 22 | WinPE-Setup-Server |
| 23 | Not applicable |
| 24 | WinPE-WDS-Tools |
| 25 | WinPE-WinReCfg |
| 26 | WinPE-WMI |

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`PackageID` Data type: `String`

Access type: [key]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageSize` Data type: `UInt32`

Access type: Read

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

For this class, the package type is PKG\_TYPE\_BOOTIMAGE (258).

`PkgFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourceFlag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PreExecCommandLine` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Command-line for the pre-execution hook injected into WinPE.

`PreExecSourceDirectory` Data type: `String`

Access type: Read/Write

Qualifiers: None

UNC path of pre-execution hook the source directory injected into WinPE.

`PreferredAddressType` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ReferencedDrivers` Data type: `SMS_Driver_Details` Array

Access type: Read/Write

Qualifiers: [lazy]

Array of details about Configuration Manager drivers included in the boot image for import.

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type: [max(15), lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ScratchSpace` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

Specifies the amount of available scratch space in WinPE. Possible values are:

| Megabytes |
| --- |
| 32 |
| 64 |
| 128 |
| 256 |
| 512 |

For additional information see [DISM Windows PE servicing command-line options](/en-us/windows-hardware/manufacture/desktop/dism-windows-pe-servicing-command-line-options).

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`SecuredScopeNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ShareName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ShareType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SourceDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SourceVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`StoredPkgPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`StoredPkgVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured
- Icon("Package.ico")

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).