---
layout: Conceptual
title: SMS_OperatingSystemInstallPackage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class
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
description: Serves as the unit of distribution for source files. The source files are used in a scripted installation of a valid operating system.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8ff5ff33-4343-ecdd-5cc6-5cdd3a438c2b
document_version_independent_id: 8f54ce0c-8499-9d0e-ff9b-57913dd69f73
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 6d94d55b-61ce-9f7f-0c95-348df0d6f8f8
---

# SMS_OperatingSystemInstallPackage Class - Configuration Manager | Microsoft Learn

The `SMS_OperatingSystemInstallPackage` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as the unit of distribution for source files that are used in a scripted installation of a valid operating system, for example, Windows Vista, on a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_OperatingSystemInstallPackage : SMS_PackageBaseclass
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

The following table shows the methods in `SMS_OperatingSystemInstallPackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS_OperatingSystemInstallPackage](addchangenotification-method-in-class-sms_operatingsysteminstallpackage) | Adds an operating system install package change notification. |
| [AddDistributionPoints Method in Class SMS_OperatingSystemInstallPackage](adddistributionpoints-method-in-class-sms_operatingsysteminstallpackage) | Adds the distribution points for the operating system install package. |
| [GetImageProperties Method in Class SMS_OperatingSystemInstallPackage](getimageproperties-method-in-class-sms_operatingsysteminstallpackage) | Reads all image properties from the specified WIM file to an XML string. |
| [RefreshPkgSource Method in Class SMS_OperatingSystemInstallPackage](refreshpkgsource-method-in-class-sms_operatingsysteminstallpackage) | Refreshes the package source at all distribution points, when the package properties have not changed. |
| [ReloadImageProperties Method in Class SMS_OperatingSystemInstallPackage](reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage) | Reloads image properties from the source WIM file and updates the database. |
| [SetSourceSite Method in Class SMS_OperatingSystemInstallPackage](setsourcesite-method-in-class-sms_operatingsysteminstallpackage) | Sets the code of the source site for the operating system install package. |
| [Unlock Method in Class SMS_OperatingSystemInstallPackage](unlock-method-in-class-sms_operatingsysteminstallpackage) | Sets the source site to the current site, unlocking the operating system install package. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

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

`ImageProperty` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

An XML string holding image properties of the source .wim file. The default value is "".

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

For this class, the package type is PKG\_TYPE\_OSINSTALLIMAGE (259).

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

`PreferredAddressType` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type:

Qualifiers: [max(15), lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

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

    To get started using this class, see How to Add an Operating System Install Package in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).