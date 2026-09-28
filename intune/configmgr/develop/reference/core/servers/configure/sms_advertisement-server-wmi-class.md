---
layout: Conceptual
title: SMS_Advertisement Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class
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
description: The SMS_Advertisement Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an advertisement.
ms.date: 2017-04-27T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 77b9d11e-9831-3c0e-274e-e41c15e371c7
document_version_independent_id: 1127b772-0b33-34cc-7438-c5dd1e53d059
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 4c73a2e5-2ba4-96ff-df13-adc21cfc6e56
---

# SMS_Advertisement Class - Configuration Manager | Microsoft Learn

The `SMS_Advertisement` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an advertisement used to announce software package programs that are available for running on clients.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Advertisement : SMS_BaseClass
{
      UInt32 ActionInProgress;
      UInt32 AdvertFlags;
      String AdvertisementID;
      String AdvertisementName;
      SMS_ScheduleToken AssignedSchedule[];
      Boolean AssignedScheduleEnabled;
      Boolean AssignedScheduleIsGMT;
      UInt32 AssignmentID;
      String CollectionID;
      String Comment;
      UInt32 DeviceFlags;
      DateTime ExpirationTime;
      Boolean ExpirationTimeEnabled;
      Boolean ExpirationTimeIsGMT;
      String HierarchyPath;
      Boolean IncludeSubCollection;
      UInt8 ISVData[];
      UInt32 ISVDataSize;
      String ISVString;
      UInt32 MandatoryCountdown;
      UInt32 OfferType;
      String PackageID;
      DateTime PresentTime;
      Boolean PresentTimeEnabled;
      Boolean PresentTimeIsGMT;
      UInt32 Priority;
      String ProgramName;
      UInt32 RemoteClientFlags;
      String SourceSite;
      UInt32 TimeFlags;
};
```

## Methods

The following table lists the methods in the `SMS_Advertisement` class.

| Method | Description |
| --- | --- |
| [GetAdvertisements Method in Class SMS_Advertisement](getadvertisements-method-in-class-sms_advertisement) | Gets the advertisement IDs that are targeted to the resource. |
| [GetNextID Method in Class SMS_Advertisement](getnextid-method-in-class-sms_advertisement) | Retrieves the ID number that will be used for the next advertisement created. |
| [RiskyDeploymentStatusMessage Method in Class SMS_Advertisement](riskydeploymentstatusmessage-method-in-class-sms_advertisement) | Sends a warning status message about a user deployment to a risky collection. |
| [SetNextID Method in Class SMS_Advertisement](setnextid-method-in-class-sms_advertisement) | Sets the ID number that will be used for the next advertisement created. |
| [SetSourceSite Method in Class SMS_Advertisement](setsourcesite-method-in-class-sms_advertisement) | Sets the source site code for the advertisement. |
| [Unlock Method in Class SMS_Advertisement](unlock-method-in-class-sms_advertisement) | Sets the source site to the current site, unlocking the advertisement. **Warning:** This method is deprecated. |

## Properties

### `ActionInProgress`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

Current action being performed on the package by Configuration Manager. Possible values are:

| Value | Description |
| --- | --- |
| 0 | NONE |
| 1 | UPDATE |
| 2 | ADD |

### `AdvertFlags`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Flags indicating how the advertisement should be announced to the user. Possible values are listed below. The default value is 0.

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x00000020 (5) | IMMEDIATE. Announce the advertisement to the user immediately. |
| 0x00000100 (8) | ONSYSTEMSTARTUP. Announce the advertisement to the user on system startup. |
| 0x00000200 (9) | ONUSERLOGON. Announce the advertisement to the user on logon. |
| 0x00000400 (10) | ONUSERLOGOFF. Announce the advertisement to the user on logoff. |
| 0x00001000 (12) | OPTIONALPREDOWNLOAD. If the selected architecture and language matches that of the client, the package content will be downloaded in advance |
| 0x00008000 (15) | WINDOWS\_CE. The advertisement is for a device client. |
| 0x00010000 (16) | ENABLE\_PEER\_CACHING. This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |
| 0x00020000 (17) | DONOT\_FALLBACK. Do not fall back to unprotected distribution points. |
| 0x00040000 (18) | ENABLE\_TS\_FROM\_CD\_AND\_PXE. The task sequence is available to removable media and the pre-boot execution environment (PXE) service point. |
| 0x00080000 (19) | APTSINTRANETONLY. |
| 0x00100000 (20) | OVERRIDE\_SERVICE\_WINDOWS. Override maintenance windows in announcing the advertisement to the user. |
| 0x00200000 (21) | REBOOT\_OUTSIDE\_OF\_SERVICE\_WINDOWS. Reboot outside of maintenance windows. |
| 0x00400000 (22) | WAKE\_ON\_LAN\_ENABLED. Announce the advertisement to the user with Wake On LAN enabled. |
| 0x00800000 (23) | SHOW\_PROGRESS. Announce the advertisement to the user showing task sequence progress. |
| 0x02000000 (25) | NO\_DISPLAY. The user should not run programs independently of the assignment. |
| 0x04000000 (26) | ONSLOWNET. Assignments are mandatory over a slow network connection. |
| 0x10000000 (28) | TARGETTOWINPE. Target this deployment to WinPE only. |
| 0x20000000 (29) | HIDDENINWINPE. Target this deployment to WinPE only but hide in WinPE. It can only be used by TS variable *SMSTSPreferredAdvertID*. |

These flags must be coordinated with the flags that are specified in the `ProgramFlags` property of the advertised program. For example, if you set ONUSERLOGOFF, the NOUSERLOGGEDIN flag in the program must be set. If the flag settings do not match, the program is not advertised. For more information, see [SMS_Program Server WMI Class](sms_program-server-wmi-class).

Setting IMMEDIATE, ONUSERLOGON, or ONUSERLOGOFF or providing an `AssignedSchedule` value makes the advertised program mandatory. A mandatory program is run automatically after the client has received the advertisement. The client cannot reject or postpone the installation.

Set the NO\_DISPLAY and ONSLOWNET bits only when the IMMEDIATE, ONUSERLOGON, or ONUSERLOGOFF bit is set or the program has an `AssignedSchedule` value.

Set NO\_DISPLAY when you do not want the user to run programs independently of the assignment. If you do not set this flag, the advertisement is shown in the list of advertisements and can be run independently of the assignment. The program can still be mandatory.

Set ONSLOWNET when assignments are mandatory over a slow network connection, for example, when a computer connects using a modem.

### `AdvertisementID`

Data type: `String`

Access type: Read/Write

Qualifiers: [key, ResID(801), ResDLL("SMS\_RSTT.dll")]

Unique auto-generated key that identifies the advertisement. The default value is "".

### `AdvertisementName`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

Unique user-friendly name for the advertisement.

`AssignedSchedule` Data type: `SMS_ScheduleToken` Array

Access type: Read/Write

Qualifiers: [max(15), lazy]

[SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class) objects indicating the time when the advertisement becomes mandatory on the clients.

### `AssignedScheduleEnabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if the schedule defined in the `AssignedSchedule` property is active. The default value is `false`.

### `AssignedScheduleIsGMT`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if the schedule defined in the `AssignedSchedule` property is in Universal Metric Time (UMT). The default value is `false`.

### `AssignmentID`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

ID of the assignment associated with the advertisement.

### `CollectionID`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

Existing collection to which the advertisement is targeted.

### `Comment`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Simple description or note about the advertisement. The default value is "".

### `DeviceFlags`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flags describing the device. Possible values are listed below. The default value is 0.

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x01000000 (24) | Always assign program to the client. |
| 0x02000000 (25) | Assign only if the device is currently connected to a high-bandwidth connection (default above 60 KBps). |
| 0x04000000 (26) | Assign only if the device is docked, that is, it is attached to a desktop that is using ActiveSync. |

### `ExpirationTime`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the advertisement is no longer available to clients. The default value is 19900101000000.000000+\*\*\*\*.

### `ExpirationTimeEnabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if the advertisement expires at the time indicated by the `ExpirationTime` property. The default value is `false`.

### `ExpirationTimeIsGMT`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if the time defined in the `ExpirationTime` property is in UMT. The default value is `false`.

### `HierarchyPath`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Reserved.

### `IncludeSubCollection`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` (default) if the advertisement is advertised to the subcollections of the specified collection.

### `ISVData`

Data type: `Uint8` Array

Access type: Read/Write

Qualifiers: [large, lazy]

Information that allows a single ISV to store data relating to an `SMS_Program` instance. There are no restrictions or defined formats for this data. However, it is important to not overwrite the property after its ISV ownership has been established. Therefore, the calling application should read the existing data in this property first. If the data does not belong to the application, it should not be modified. Any ISV or application owner who is using this property should include an identifier in the data so that ownership can be easily established.

### `ISVDataSize`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

The size of the data represented by the `ISVData` property. The default value is 0.

### `ISVString`

Data type: `String`

Access type: Read/Write

Qualifiers: none

String for partner extensibility.

### `MandatoryCountdown`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Duration, in minutes, to show operating system deployment user notification mandatory schedule countdown. The default value is 0.

### `OfferType`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Advertisement type that indicates that the advertisement is targeted to users.

| Value | Description |
| --- | --- |
| 0 | Required |
| 2 | Available |

### `PackageID`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

ID for an existing package associated with the advertisement. The value must be in uppercase.

### `PresentTime`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the advertisement is made available to clients. The default value is 19900101000000.000000+\*\*\*\*.

### `PresentTimeEnabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` (default) if the present time is enforced by Configuration Manager.

### `PresentTimeIsGMT`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: [lazy]

`true` if the time defined in the `PresentTime` property is in UMT. The default value is `false`.

### `Priority`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The priority used in replicating the advertisement to child sites. Possible values are listed below. The default value is NORMAL (2).

| Value | Description |
| --- | --- |
| 1 | HIGH |
| 2 | NORMAL |
| 3 | LOW |

### `ProgramName`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

A program within the specified package (`PackageID`) to be advertised.

### `RemoteClientFlags`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Flags specifying how the program should run when the client is connected either locally or remotely to a distribution point. Possible values are listed below. The default value is 48.

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x00000001 (0) | BATTERY\_POWER. Run the program by using battery power. This value is currently unused. |
| 0x00000002 (1) | RUN\_FROM\_CD. Run the program from CD. This value is currently unused. |
| 0x00000004 (2) | DOWNLOAD\_FROM\_CD. Download the program from CD. This value is currently unused. |
| 0x00000008 (3) | RUN\_FROM\_LOCAL\_DISPPOINT. Run the program from the local distribution point. |
| 0x00000010 (4) | DOWNLOAD\_FROM\_LOCAL\_DISPPOINT. Download the program from the local distribution point. |
| 0x00000020 (5) | DONT\_RUN\_NO\_LOCAL\_DISPPOINT. Do not run the program if there is no local distribution point. |
| 0x00000040 (6) | DOWNLOAD\_FROM\_REMOTE\_DISPPOINT. Download the program from the remote distribution point. |
| 0x00000080 (7) | RUN\_FROM\_REMOTE\_DISPPOINT. Run the program from the remote distribution point. |
| 0x00000100 (8) | DOWNLOAD\_ON\_DEMAND\_FROM\_LOCAL\_DP. Download the program on demand from the local distribution point. This is only applicable for task sequences. |
| 0x00000200 (9) | DOWNLOAD\_ON\_DEMAND\_FROM\_REMOTE\_DP. Download the program on demand from the remote distribution point. This is only applicable for task sequences. |
| x00000400 (10) | BALLOON\_REMINDERS\_REQUIRED. Balloon reminders are required. |
| 0x00000800 (11) | RERUN\_ALWAYS. Always rerun the program. |
| 0x00001000 (12) | RERUN\_NEVER. Never rerun the program. |
| 0x00002000 (13) | RERUN\_IF\_FAILED. Rerun the program if execution previously failed. |
| 0x00004000 (14) | RERUN\_IF\_SUCCEEDED. Rerun the program if execution previously succeeded. |
| 0x00008000 (15) | PERSIST\_ON\_WRITE\_FILTER\_DEVICES  This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |
| 0x00020000 (17) | DON'T\_FALLBACK  This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |
| 0x00040000 (18) | DP\_ALLOW\_METERED\_NETWORK  This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later. |

### `SourceSite`

Data type: `String`

Access type: Read-only

Qualifiers: [read]

Three-letter site code of the site where the advertisement originates.

### `TimeFlags`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, bits]

Reserved for internal use. Flags that duplicate the information in the time-related properties. Possible values are listed below. For example, ENABLE\_PRESENT is set when `PresentTimeEnabled` equals `true`.

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x00000001 (0) | ENABLE\_PRESENT |
| 0x00000002 (1) | ENABLE\_EXPIRATION |
| 0x00000004 (2) | ENABLE\_AVAILABLE |
| 0x00000008 (3) | ENABLE\_UNAVAILABLE |
| 0x00000010 (4) | ENABLE\_MANDATORY |
| 0x00000020 (5) | GMT\_PRESENT |
| 0x00000040 (6) | GMT\_EXPIRATION |
| 0x00000080 (7) | GMT\_AVAILABLE |
| 0x00000100 (8) | GMT\_UNAVAILABLE |
| 0x00000200 (9) | GMT\_MANDATORY |

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Although there are no other key properties, the properties `AdvertisementName`, `CollectionID`, `PackageID`, and `ProgramName` are qualified as NOT\_NULL, and values must be supplied. Your application cannot update these properties after a class instance is created. To change these values, the application must delete the instance and create a new instance with the correct values.

## Requirements

### Runtime requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).