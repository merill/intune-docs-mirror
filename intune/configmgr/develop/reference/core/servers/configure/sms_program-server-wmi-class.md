---
layout: Conceptual
title: SMS_Program Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class
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
description: Learn how to represent a program or command to run when software is distributed to a client computer using SMS_Program class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 80ca83db-8d56-0d61-a1c3-dc17355b0c37
document_version_independent_id: 4d0c4c09-4f21-3036-567a-a5fb2bc5d158
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dfe61477-32d5-8b6c-ac73-d31d7d3f494c
---

# SMS_Program Class - Configuration Manager | Microsoft Learn

The `SMS_Program` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a program or command to run when software is distributed to a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Program : SMS_BaseClass
{
     UInt32 ActionInProgress;
     String ApplicationHierarchy;
     String CommandLine;
     String Comment;
     String DependentProgram;
     String Description;
     UInt32 DeviceFlags;
     String DiskSpaceReq;
     String DriveLetter;
     UInt32 Duration;
     UInt8 ExtendedData[];
     UInt32 ExtendedDataSize;
     UInt8 Icon[];
     UInt32 IconSize;
     UInt8 ISVData[];
     UInt32 ISVDataSize;
     String ISVString;
     String MSIFilePath
     String MSIProductID
     String PackageID;
     String PackageName
     UInt32 PackageType
     String PackageVersion
     UInt32 ProgramFlags;
     String ProgramName;
     String RemovalKey;
     String Requirements;
     UInt32 SecuredTypeID
     SMS_OS_Details SupportedOperatingSystems[];
     UInt32   TransformReadiness=0;
     Datetime TransformAnalysisDate;
     String   TransformDtID;
     String WorkingDirectory;
};
```

## Methods

The `SMS_Program` class doesn't define any methods.

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

Current action being performed on the package that is associated with the program by Configuration Manager. Possible values are:

| Value | Description |
| --- | --- |
| 0 | NONE |
| 1 | UPDATE |
| 2 | ADD |
| 3 | DELETE |

Use this property in a WHERE clause to filter out programs that have been marked for deletion but haven't yet been deleted. For more information, see the Remarks section later in this topic.

`ApplicationHierarchy` Data type: `String`

Access type: Read/Write

Qualifiers: None

The application hierarchy for the program. The default value is "".

`CommandLine` Data type: `String`

Access type: Read/Write

Qualifiers: None

The command line that runs when the program is started. The default value is "".

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Comment that describes the program in the Configuration Manager console. The default value is "".

`DependentProgram` Data type: `String`

Access type: Read/Write

Qualifiers: None

A formatted text string defining any program that should be run prior to running this program. The format is defined as &lt;PackageID&gt;;;&lt;ProgramName&gt;. If the program is in the same package, the calling application can simply specify ;;&lt;ProgramName&gt;. The default value is "".

The dependency is maintained only for the first time that the program runs. After the program has run, the dependency is ignored. For example, you can't create a recurring scheduled job for which the dependency is maintained for each program run.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Not used.

`DeviceFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flags describing the device associated with the program. Possible values are:

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x01000000 (24) | Always assign program to the client. |
| 0x02000000 (25) | Assign only if the device is currently connected to a high-bandwidth connection (default above 60 KBps). |
| 0x04000000 (26) | Assign only if the device is docked, that is, it's attached to a desktop that is using ActiveSync. |

`DiskSpaceReq` Data type: `String`

Access type: Read/Write

Qualifiers: None

Approximate disk space that the program requires. The format is "&lt;size&gt; &lt;KB|MB|GB&gt;". The default value is "".

This information is used in the Configuration Manager console and the advertisement to provide alerts about program disk space requirements. The user can then decide to accept the advertisement or perform some disk management task first.

`DriveLetter` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("1"), Range("a-z")]

Drive letter (one character in the range a-z) that the program maps to and runs from. The default value is "".

`Duration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The approximate duration, in minutes, of program execution on the client computer. Specify this value as a whole number greater than or equal to 0 (default) or as Unknown (not recommended). If the property is set to Unknown, Configuration Manager sets the maximum allowed run time as 720 minutes (12 hours). For more information, see the Remarks section later in this topic.

Note

On client computers, the specified value for published programs appears in `Run Advertised Programs` in Control Panel.

`ExtendedData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

The XML blob for image deployment.

`ExtendedDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

The extended data size, in bytes. The default value is 0.

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large]

Icon information associated with the program icon, as displayed in the Configuration Manager console.

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

Size, in bytes, of the program icon. Set this property to 0 to clear the icon.

`ISVData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

Information that allows a single ISV to store data relating to an `SMS_Program` object.

There are no restrictions or defined formats for the ISV data. However, it's important to not overwrite the property after the ISV ownership has been established. Your application should read the existing data in this property first. If the data doesn't belong to the application, it shouldn't be modified. You should include an identifier in the data for the program so that ownership can be established easily.

`ISVDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

The size, in bytes, of the data stored in `ISVData`. The default value is 0.

`ISVString` Data type: `String`

Access type: Read/Write

Qualifiers: none

String for partner extensibility.

`MSIFilePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

The file path of the Windows Installer package with which the program is associated. The default value is "".

`MSIProductID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The product ID of the Windows Installer package with which the program is associated. The default value is "".

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

ID of an existing package with which to associate the program. For more information, see the Remarks section later in this topic.

`PackageName` Data type: `String`

Access type: Read/Write

Qualifiers: [None]

The name of the package the program belongs to.

`PackageType` Data type: `String`

Access type: Read/Write

Qualifiers: [None]

The type of the package the program belongs to.

| Value | Description |
| --- | --- |
| 0 | Regular software distribution package. |
| 3 | Driver package. |
| 4 | Task sequence package. |
| 5 | Software update package. |
| 6 | Device setting package. |
| 257 | Image package. |
| 258 | Boot image package. |
| 259 | Operating system install package. |

`PackageVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [None]

The version of the package the program belongs to.

`ProgramFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Flags identifying the installation characteristics of the program. Possible values are listed below. The default values are EVERYUSER, USEUNCPATH, USERCONTEXT, and UNATTENDED.

Note

When using `SMS_Program` programmatically, ensure that no conflicting values are selected. For example, NOUSERLOGGEDIN and USERCONTEXT should not be used together.

Possible values are:

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x00000001 (0) | AUTHORIZED\_DYNAMIC\_INSTALL. The program is authorized for dynamic install. |
| 0x00000002 (1) | USECUSTOMPROGRESSMSG. The task sequence shows a custom progress user interface message. |
| 0x00000010 (4) | DEFAULT\_PROGRAM. This is a default program |
| 0x00000020 (5) | DISABLEMOMALERTONRUNNING. Disables MOM alerts while the program runs. |
| 0x00000040 (6) | MOMALERTONFAIL. Generates MOM alert if the program fails. |
| 0x00000080 (7) | RUN\_DEPENDANT\_ALWAYS. If set, this program's immediate dependent should always be run. |
| 0x00000100 (8) | WINDOWS\_CE. Indicates a device program. If set, the program isn't offered to desktop clients. |
| 0x00000200 (9) | This value isn't used. |
| 0x00000400 (10) | COUNTDOWN. The countdown dialog isn't displayed. |
| 0x00000800 (11) | FORCERERUN. This value isn't used. |
| 0x00001000 (12) | DISABLED. The program is disabled. |
| 0x00002000 (13) | UNATTENDED. The program requires no user interaction. |
| 0x00004000 (14) | USERCONTEXT. The program can run only when a user is logged on. |
| 0x00008000 (15) | ADMINRIGHTS. The program must be run as the local Administrator account. |
| 0x00010000 (16) | EVERYUSER. The program must be run by every user for whom it's valid. Valid only for mandatory jobs. |
| 0x00020000 (17) | NOUSERLOGGEDIN. The program is run only when no user is logged on. |
| 0x00040000 (18) | OKTOQUIT. The program will restart the computer. |
| 0x00080000 (19) | OKTOREBOOT. Configuration Manager restarts the computer when the program has finished running successfully. |
| 0x00100000 (20) | USEUNCPATH. Use a UNC path (no drive letter) to access the distribution point. |
| 0x00200000 (21) | PERSISTCONNECTION. Persists the connection to the drive specified in the DriveLetter property. The USEUNCPATH bit flag must not be set. |
| 0x00400000 (22) | RUNMINIMIZED. Run the program as a minimized window. |
| 0x00800000 (23) | RUNMAXIMIZED. Run the program as a maximized window. |
| x01000000 (24) | HIDEWINDOW. Hide the program window. |
| 0x02000000 (25) | OKTOLOGOFF. Logoff user when program completes successfully. |
| 0x04000000 (26) | RUNACCOUNT. This value isn't used. |
| 0x08000000 (27) | ANY\_PLATFORM. Override check for platform support. |
| 0x10000000 (28) | STILL\_RUNNING. This value isn't used. |
| 0x20000000 (29) | SUPPORT\_UNINSTALL. Run uninstall from the registry key when the advertisement expires. |
| 0x40000000 (30) | The platform isn't supported. |
| 0x80000000 (31) | SHOW\_IN\_ARP. This value isn't used. |

`ProgramName` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Unique name that represents this program.

`RemovalKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

Registry key that identifies the uninstall script for the program. The script must reside in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall` registry path. The default value is "".

`Requirements` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of any extra requirements of the program. The default value is "".

`SecuredTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [None]

Secured type of related package.

`SupportedOperatingSystems` Data type: `SMS_OS_Details` Array

Access type: Read/Write

Qualifiers: [lazy]

[SMS_OS_Details Server WMI Class](sms_os_details-server-wmi-class) objects representing the operating systems on which the program can run.

If you don't specify ANY\_PLATFORM in the `ProgramFlags` property, you must specify one or more supported operating systems. [SMS_SupportedPlatforms Server WMI Class](sms_supportedplatforms-server-wmi-class) defines the list of platforms that Configuration Manager supports.

`TransformAnalysisDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [None]

For internal use only.

`TransformDtID` Data type: `String`

Access type: Read/Write

Qualifiers: [None]

For internal use only.

`TransformReadiness` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [None]

For internal use only.

`WorkingDirectory` Data type: `String`

Access type: Read/Write

Qualifiers: None

The location from which the program runs. The default value is "".

The working directory can be an absolute path on the client or a path relative to the distribution point folder that contains the package. If a working directory isn't specified, Configuration Manager uses the default distribution point folder.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

A program is always associated with a parent package and typically represents the installation program for the package. More than one program can be associated with the same package. The application uses the `PackageID` property to make this association. Your application can't change this property after the `SMS_Program` object is created. To associate the program with a different package, the application must delete the object and create a new object with a new `PackageID` value.

When your application deletes an `SMS_Program` object, it isn't deleted until its related components, such as its advertisements, are deleted. Instead, Configuration Manager sets the `ActionInProgress` property to DELETE (3) to mark the program for deletion. To ensure that a query doesn't retrieve programs that have been marked for deletion, add this case to the WHERE clause.

Important

If you are using maintenance windows for the collection on which the program is run, a conflict can occur if the value of the `Duration` property is longer than the scheduled maintenance window. If this property is set to Unknown, the program starts during the maintenance window, but continues to run until it completes or fails after the maintenance window is closed.

It's recommended that you not set the `Duration` property to Unknown because this property is used for the following two important purposes:

- To monitor the results of the program.
- To determine if the program will be launched when maintenance windows have been defined on the client computers.

    If your application sets the `Duration` property but program run time exceeds this duration, then Configuration Manager stops monitoring the program but doesn't terminate the program. This allows Configuration Manager to continue with other software distribution functions, such as running other advertised programs. The manager does not:
- Stop the program.
- Free any drives that have been mapped for the advertised program.
- Free any network connections made for the advertised program.
- Free operating system resources used by Configuration Manager when advertised programs are running.

    For more information, see [About Maintenance Windows](../../../../core/servers/configure/about-maintenance-windows).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).