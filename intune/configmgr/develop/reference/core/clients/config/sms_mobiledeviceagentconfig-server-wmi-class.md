---
layout: Conceptual
title: SMS_MobileDeviceAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_mobiledeviceagentconfig-server-wmi-class
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
description: Learn how to specify general settings for mobile devices in Configuration Manager using the SMS_MobileDeviceAgentConfig class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c6ec110f-6e0e-7234-7737-45e8819739dc
document_version_independent_id: ae497aa8-7e27-6c37-37af-ee41d40ad2e8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_mobiledeviceagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_mobiledeviceagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_mobiledeviceagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2a1c2ef7-ce6c-2c87-93c2-f7e3cd381eea
---

# SMS_MobileDeviceAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_MobileDeviceAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies general settings for mobile devices.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MobileDeviceAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 DeviceEnrollmentProfileID;
    UInt32 EnableDeviceEnrollment;
    Boolean EnableFileCollection;
    Boolean EnableHardwareInventory;
    UInt32 EnableModernDeviceEnrollment;
    Boolean EnableSoftwareDistribution;
    Boolean EnableSoftwareInventory;
    UInt32 FailureRetryCount;
    String FailureRetryInterval;
    String FileCollectionExcludeCompressed[];
    String FileCollectionExcludeEncrypted[];
    String FileCollectionFilter[];
    String FileCollectionInterval;
    String FileCollectionPath[];
    String FileCollectionSubdirectories[];
    String HardwareInventoryInterval;
    UInt32 MDMPollInterval;
    UInt32 ModernDeviceEnrollmentProfileID;
    String PollingInterval;
    String PollServer;
    String SoftwareInventoryExcludeCompressed[];
    String SoftwareInventoryExcludeEncrypted[];
    String SoftwareInventoryFilter[];
    String SoftwareInventoryInterval;
    String SoftwareInventoryPath[];
    String SoftwareInventorySubdirectories[];
};
```

## Methods

The `SMS_MobileDeviceAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Mobile Device Agent ID is 12.

`DeviceEnrollmentProfileID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Mobile device enrollment profile ID.

`EnableDeviceEnrollment` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Allow users to enroll mobile devices.

`EnableFileCollection` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable file collection.

`EnableHardwareInventory` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable hardware inventory.

`EnableModernDeviceEnrollment` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Enables enrollment for modern devices.

`EnableSoftwareDistribution` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable software distribution on devices.

`EnableSoftwareInventory` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable software inventory on devices.

`FailureRetryCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

FailureRetryCount description.

`FailureRetryInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

FailureRetryInterval.

`FileCollectionExcludeCompressed` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

When collecting files, exclude compressed files.

`FileCollectionExcludeEncrypted` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

When collecting files, exclude encrypted files.

`FileCollectionFilter` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

FileCollectionFilter.

`FileCollectionInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

FileCollectionInterval.

`FileCollectionPath` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

FileCollectionPath.

`FileCollectionSubdirectories` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

FileCollectionSubdirectories.

`HardwareInventoryInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

HardwareInventoryInterval.

`MDMPollInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Polling interval for mobile device management.

`ModernDeviceEnrollmentProfileID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

ID of the enrollment profile that allows users to enroll modern devices.

`PollingInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

Policy polling interval, in minutes.

`PollServer` Data type: `String`

Access type: Read/Write

Qualifiers: none

PollServer.

`SoftwareInventoryExcludeCompressed` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

When inventorying files, exclude compressed files.

`SoftwareInventoryExcludeEncrypted` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

When inventorying files, exclude encrypted files.

`SoftwareInventoryFilter` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

SoftwareInventoryFilter.

`SoftwareInventoryInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

SoftwareInventoryInterval.

`SoftwareInventoryPath` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

SoftwareInventoryPath.

`SoftwareInventorySubdirectories` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

SoftwareInventorySubdirectories.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).