---
layout: Conceptual
title: SMS_TaskSequencePackage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class
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
description: In Configuration Manager, the SMS_TaskSequencePackage WMI class is an SMS Provider server class that represents a task sequence package that defines the steps to run for the task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3b841dbd-0946-44d7-89c9-1a715865b1af
document_version_independent_id: d0ba693c-f31a-7473-94a1-4f20eb9012ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e4af9bd1-3b3f-5a99-0a4a-7aa774a39684
---

# SMS_TaskSequencePackage Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequencePackage` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a task sequence package that defines the steps to run for the task sequence.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequencePackage : SMS_PackageBaseclass
{
      UInt32 ActionInProgress;
      String AlternateContentProviders;
      String BootImageID;
      String Category;
      String CustomProgressMsg;
      String DependentProgram;
      String Description;
      UInt32 Duration;
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
      String PackageID;
      UInt32 PackageSize;
      UInt32 PackageType;
      UInt32 PkgFlags;
      UInt32 PkgSourceFlag;
      String PkgSourcePath;
      String PreferredAddressType;
      UInt32 Priority;
      UInt32 ProgramFlags;
      SMS_TaskSequence_Reference References[];
      Boolean RefreshPkgSourceFlag;
      SMS_ScheduleToken RefreshSchedule[];
      String SecuredScopeNames[];
      String SedoObjectVersion;
      UInt32 ReferencesCount;
      String Reserved;
      String Sequence;
      String ShareName;
      UInt32 ShareType;
      DateTime SourceDate;
      String SourceSite;
      UInt32 SourceVersion;
      String StoredPkgPath;
      UInt32 StoredPkgVersion;
      SMS_OS_Details SupportedOperatingSystems[];
      UInt32 TaskSequenceFlags;
      UInt32 Type;
      String Version;
};
```

## Methods

The following table shows the methods in `SMS_TaskSequencePackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS_TaskSequencePackage](addchangenotification-method-in-class-sms_tasksequencepackage) | Adds a task sequence package change notification. |
| [AddDistributionPoints Method in Class SMS_TaskSequencePackage](adddistributionpoints-method-in-class-sms_tasksequencepackage) | Adds the distribution points for the task sequence package. |
| [CheckReferencesShareType Method in Class SMS_TaskSequencePackage](checkreferencessharetype-method-in-class-sms_tasksequencepackage) | Checks all referred package for this task sequence and returns all that are not shared. |
| [GetClientConfigPolicies Method in Class SMS_TaskSequencePackage](getclientconfigpolicies-method-in-class-sms_tasksequencepackage) | Gets all site-wide client configuration policies and their corresponding policy assignments. |
| [GetContentHash Method in Class SMS_TaskSequencePackage](getcontenthash-method-in-class-sms_tasksequencepackage) | Gets the hash of specific Configuration Manager content. |
| [GetPackageDefaultHash Method in Class SMS_TaskSequencePackage](getpackagedefaulthash-method-in-class-sms_tasksequencepackage) | Gets the hash of a Configuration Manager package. |
| [GetPackageHash Method in Class SMS_TaskSequencePackage](getpackagehash-method-in-class-sms_tasksequencepackage) | Gets the certificate hash for the task sequence package. |
| [GetSequence Method in Class SMS_TaskSequencePackage](getsequence-method-in-class-sms_tasksequencepackage) | Gets a task sequence from a task sequence package. |
| [GetTsPolicies Method in Class SMS_TaskSequencePackage](gettspolicies-method-in-class-sms_tasksequencepackage) | Gets all policies associated with the specified task sequence. |
| [GetTsPoliciesSaMedia Method in Class SMS_TaskSequencePackage](gettspoliciessamedia-method-in-class-sms_tasksequencepackage) | Gets all policies associated with the specified task sequence. |
| [GetTSRelatedToDriverCategory Method in Class SMS_TaskSequencePackage](gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage) | Get task sequence packages related to the specified category. |
| [ImportSequence Method in Class SMS_TaskSequencePackage](importsequence-method-in-class-sms_tasksequencepackage) | Imports an `SMS_TaskSequence` object based on the provided XML. |
| [RefreshPkgSource Method in Class SMS_TaskSequencePackage](refreshpkgsource-method-in-class-sms_tasksequencepackage) | Refreshes the package source at all distribution points when the package properties have not changed. |
| [SetSequence Method in Class SMS_TaskSequencePackage](setsequence-method-in-class-sms_tasksequencepackage) | Updates a task sequence package with the input task sequence. |
| [SetSourceSite Method in Class SMS_TaskSequencePackage](setsourcesite-method-in-class-sms_tasksequencepackage) | Sets the code of the source site for the task sequence package. |
| [Unlock Method in Class SMS_TaskSequencePackage](unlock-method-in-class-sms_tasksequencepackage) | Sets the source site to the current site, which unlocks the task sequence package. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: [large, lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`BootImageID` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

ID of the boot image package if the task sequence contains a reference to a boot image in the `References` property. For information about the boot image package, see [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class).

`Category` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Task sequence package category. The default value is "". The category for the package is assigned using the `Category` property of [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class).

`CustomProgressMsg` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

A custom progress message specified in the Configuration Manager console.

`DependentProgram` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

A formatted text string defining any program that should be run before the current program. The format is "&lt;PackageID&gt;;;&lt;ProgramName&gt;". For more information, see [SMS_Program Server WMI Class](../core/servers/configure/sms_program-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Duration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The approximate time, in minutes, that the program takes to run. The default value is 0.

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

`LocalizedCategoryInstanceNames` Data type: `String Array`

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

Access type: Read

Qualifiers [key]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageSize` Data type: `UInt32`

Access type: Read

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

For this class, the package type is PKG\_TYPE\_TASK\_SEQUENCE (4).

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

`ProgramFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Flags identifying the installation characteristics of the program. The default flags are default program, UNATTENDED, UNCPATH, HIDEWINDOW, ADMINRIGHTS, and ANY\_PLATFORM. The default value is 152084496.

| Bit | Decimal | Hexadecimal | Description |
| --- | --- | --- | --- |
| 0 | 1 | 0x00000001 | AUTHORIZED\_DYNAMIC\_INSTALL. The program is authorized for dynamic installation. |
| 1 | 2 | 0x00000002 | USE\_CUSTOM\_PROGRESS\_MSG. The program uses a customized progress message. |
| 8 | 256 | 0x00000100 | WINDOWS\_CE. Use Windows CE as the device program. If this value is set, the program is not offered to desktop clients. |
| 9 | 512 | 0x00000200 | RUN\_DEPENDANT\_ALWAYS. Always run the immediate dependent of the program. |
| 10 | 1024 | 0x00000400 | COUNTDOWN. Display the countdown dialog box. |
| 12 | 4096 | 0x00001000 | DISABLED. The program is disabled. |
| 13 | 8192 | 0x00002000 | UNATTENDED. The program requires no user interaction. |
| 14 | 16384 | 0x00004000 | USERCONTEXT. The program needs to run in the user context. Always set the value to 0. |
| 15 | 32768 | 0x00008000 | ADMINRIGHTS. The program must run under administrator rights. |
| 16 | 65536 | 0x00010000 | EVERYUSER. The program must be run by every user for whom it is valid. This setting is valid only for mandatory jobs. Always set the value to 0. |
| 17 | 131072 | 0x00020000 | NOUSERLOGGEDIN. The program is run only when no user is logged on. |
| 18 | 262144 | 0x00040000 | OKTOQUIT. Program shutdown is enabled. Always set the value to 0. |
| 19 | 524288 | 0x00080000 | OKTOREBOOT. Computer reboot is enabled. Always set the value to 0. |
| 20 | 1048576 | 0x00100000 | USEUNCPATH. Program access uses a Universal Naming Convention (UNC) path. |
| 21 | 2097152 | 0x00200000 | PERSISTCONNECTION. The program connection is persisted. Always set the value to 0. |
| 22 | 4194304 | 0x00400000 | RUNMINIMIZED. Maximize the program window. Always set the value to 0. |
| 23 | 8388608 | 0x00800000 | RUNMAXIMIZED. Minimize the program window. Always set the value to 0. |
| 24 | 16777216 | 0x01000000 | HIDEWINDOW. Hide the program window. |
| 25 | 33554432 | 0x02000000 | OKTOLOGOFF. Logoff is enabled. Always set the value to 0. |
| 26 | 67108864 | 0x04000000 | RUNACCOUNT. Run the program using account access. |
| 27 | 134217728 | 0x08000000 | ANY\_PLATFORM. The program can run on any operating system. |
| 28 | 268435456 | 0x10000000 | STILL\_RUNNING. The program is currently running. |
| 29 | 536870912 | 0x20000000 | SUPPORT\_UNINSTALL. The program has an uninstall utility. Always set the value to 0. |
| 31 | 2147483648 | 0x80000000 | SHOW\_IN\_ARP. Display the program in Add or Remove Programs. |

`References` Data type: `SMS_TaskSequence_Reference` Array

Access type: Read-only

Qualifiers: [lazy, read]

[SMS_TaskSequence_Reference Server WMI Class](sms_tasksequence_reference-server-wmi-class) objects representing the packages/programs and applications referred to by steps in the task sequence.

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type:

Qualifiers: [max(15), lazy]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ReferencesCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Size of the array indicated by the `References` property. This represents the number of package/programs and applications referred by the task sequence.

`Reserved` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Used internally by the SMS Provider.

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Sequence` Data type: `String`

Access type: Read-only

Qualifiers: [lazy, read]

XML-formatted data containing task sequence information.

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

`SupportedOperatingSystems` Data type: `SMS_OS_Details` Array

Access type: Read/Write

Qualifiers: [lazy]

SMS\_OS\_Details Server WMI Class objects that describe details for the platforms on which the program can run.

`TaskSequenceFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy, bits("DANGLING\_REF(0)")]

Flags indicating task sequence package conditions. The only flag currently defined is DANGLING\_REF (bit 0).

| Bit | Description |
| --- | --- |
| 0 | Set if the task sequence references a package that is not defined on the site. |

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: [lazy, read]

The type of task sequence represented by the package. Possible values are:

| Value | Description |
| --- | --- |
| 1 | Generic task sequence |
| 2 | Operating system deployment task sequence |

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured
- Icon("Package.ico")

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    To get started using this class, see How to Create an Operating System Deployment Task Sequence Package.

    You create an operating system deployment task sequence package by creating an instance of the `SMS_TaskSequencePackage` class to hold a task sequence. The task sequence itself is created by using the Operating System Deployment Task Sequence Object Model, and it is associated with the task sequence package by using the [SetSequence Method in Class SMS_TaskSequencePackage](setsequence-method-in-class-sms_tasksequencepackage) method. The package is advertised to clients who can then run the task sequence. For more information, see How to Create an Operating System Deployment Task Sequence Package.

    For more information about the task sequence WMI objects, see About Operating System Deployment Task Sequences.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).