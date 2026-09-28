---
layout: Conceptual
title: SMS_DeviceEnrollmentProfile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_deviceenrollmentprofile-server-wmi-class
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
description: The SMS_DeviceEnrollmentProfile Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a device enrollment profile in the database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 14c42587-9968-7951-c49e-63e78242676a
document_version_independent_id: 3ded6eb4-2636-b37d-693c-d7f43bad0a66
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_deviceenrollmentprofile-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_deviceenrollmentprofile-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_deviceenrollmentprofile-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d961517b-9320-d78f-d1e3-0b556ecef0dd
---

# SMS_DeviceEnrollmentProfile Class - Configuration Manager | Microsoft Learn

The `SMS_DeviceEnrollmentProfile` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a device enrollment profile in the database.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceEnrollmentProfile : SMS_BaseClass
{
    String CertAuthorities[];
    String CertCIUniqueID;
    String Description;
    String DevicesContainerDN;
    String DevicesGroup;
    String EnrollmentSiteCode;
    String ManagementSiteCode;
    String Name;
    UInt32 ProfileID;
    UInt32 ProfileType;
    UInt32 RecordExpiryMinutes;
};
```

## Methods

The `SMS_DeviceEnrollmentProfile` class does not define any methods.

## Properties

`CertAuthorities` Data type: `String` Array

Access type: Read/Write

Qualifiers: none

Each CA must have a properly configured template of CertTemplateName, and must chain to the root certificate trusted by the server hosting the ManagementUri.

`CertCIUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for a certificate configuration item.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Text describing the profile.

`DevicesContainerDN` Data type: `String`

Access type: Read/Write

Qualifiers: none

The location where device accounts are created.

`DevicesGroup` Data type: `String`

Access type: Read/Write

Qualifiers: none

The Security Group with enroll rights on the CA template.

`EnrollmentSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

The site code where devices should enroll.

`ManagementSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

The site code from where device should be managed.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the profile. This name must be unique.

`ProfileID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Unique identifier to differentiate the profile.

`ProfileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The type of the profile.

| Value | Profile type |
| --- | --- |
| 1 | DM |
| 2 | AMT |

`RecordExpiryMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of minutes for which the record is valid.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).