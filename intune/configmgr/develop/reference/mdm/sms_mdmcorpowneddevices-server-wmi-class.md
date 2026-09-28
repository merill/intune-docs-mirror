---
layout: Conceptual
title: SMS_MDMCorpOwnedDevices Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmcorpowneddevices-server-wmi-class
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
description: The SMS_MDMCorpOwnedDevices WMI class represents On-premises Mobile Device Management (MDM) corporate owned devices.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d73d8cbb-0ec5-24b2-1de3-a27f07f4f5b9
document_version_independent_id: 15142750-82bd-4cba-231d-005d50a5833e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmcorpowneddevices-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmcorpowneddevices-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmcorpowneddevices-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e718b8cb-1728-0c30-7ce1-f92410c93bb7
---

# SMS_MDMCorpOwnedDevices Class - Configuration Manager | Microsoft Learn

The `SMS_MDMCorpOwnedDevices` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) corporate owned devices.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMCorpOwnedDevices : SMS_BaseClass
{
    DateTime ActualEnrollmentProfileAssignedTime;
    String ActualEnrollmentProfileId;
    String AssetTag;
    String Color;
    String Description;
    String DeviceAssignedBy;
    DateTime DeviceAssignedDate;
    String DeviceId;
    String DeviceName;
    UInt32 DeviceType;
    UInt32 DiscoverySources;
    String EnrollmentPackageId;
    UInt32 EnrollmentStatus;
    UInt32 EnrollmentType;
    String ExchangeDeviceId;
    String IMEI;
    DateTime LastUpdateTime;
    String Model;
    String OSVersion;
    DateTime ProfileAssignedTime;
    String ProfileName;
    DateTime ProfilePushedTime;
    UInt32 ProfileStatus;
    String ProfileUuid;
    DateTime RequestEnrollmentProfileAssignedTime;
    String RequestEnrollmentProfileId;
    String SerialNumber;
    String UniqueId;
};

```

## Methods

The following table lists the methods in the `SMS_MDMCorpOwnedDevices` class.

| Method | Description |
| --- | --- |
| [UpdateProfileIDForDevices Method in Class SMS_MDMCorpOwnedDevices](updateprofileidfordevices-method-in-class-sms_mdmcorpowneddevices) | Updates the profile IDs for device serial numbers. |

## Properties

`ActualEnrollmentProfileAssignedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time that the device enrolled to the profile.

`ActualEnrollmentProfileId` Data type: `String`

Access type: Read/Write

Qualifiers: none

The profile to which the device enrolled.

`AssetTag` Data type: `String`

Access type: Read/Write

Qualifiers: none

Asset tag of the device.

`Color` Data type: `String`

Access type: Read/Write

Qualifiers: none

Color of the device.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the device.

`DeviceAssignedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

The Apple ID of the person who assigned the device.

`DeviceAssignedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time stamp when the device was assigned to the MDM server.

`DeviceId` Data type: `String`

Access type: Read/Write

Qualifiers: none

The device ID of the device

`DeviceName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the device.

`DeviceType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The platform of the device.

`DiscoverySources` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Discovery source of the device.

`EnrollmentPackageId` Data type: `String`

Access type: Read/Write

Qualifiers: none

The enrollment package ID.

`EnrollmentStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Enrollment status of the device.

`EnrollmentType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The corporate enrollment type.

`ExchangeDeviceId` Data type: `String`

Access type: Read/Write

Qualifiers: none

The Exchange device ID of the device.

`IMEI` Data type: `String`

Access type: Read/Write

Qualifiers: none

The IMEI number of the device.

`LastUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time stamp when the device was last updated.

`Model` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model of the device.

`OSVersion` Data type: `String`

Access type: Read/Write

Qualifiers: none

Operating system version on the device.

`ProfileAssignedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time at which the profile was assigned.

`ProfileName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the profile.

`ProfilePushedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time that the profile was pushed from Apple.

`ProfileStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Status of the profile from Apple.

`ProfileUuid` Data type: `String`

Access type: Read/Write

Qualifiers: none

UUID of the profile currently assigned to the device.

`RequestEnrollmentProfileAssignedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time that the profile was requested to be assigned to the device.

`RequestEnrollmentProfileId` Data type: `String`

Access type: Read/Write

Qualifiers: none

The profile to which the device is assigned.

`SerialNumber` Data type: `String`

Access type: Read/Write

Qualifiers: none

Serial number of the device.

`UniqueId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The unique ID of a device.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).