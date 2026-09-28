---
layout: Conceptual
title: SMS_MDMCorpEnrollmentProfiles Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmcorpenrollmentprofiles-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) corporate enrollment profiles.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 79ae9f3c-570b-8e93-019e-4be7eb1df8d3
document_version_independent_id: 1d7722eb-e757-6d42-bf8f-e61b01dfab11
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmcorpenrollmentprofiles-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmcorpenrollmentprofiles-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmcorpenrollmentprofiles-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fd6524b0-c4c2-f78d-d00c-a20f35835eb2
---

# SMS_MDMCorpEnrollmentProfiles Class - Configuration Manager | Microsoft Learn

The `SMS_MDMCorpEnrollmentProfiles` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) corporate enrollment profiles.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMCorpEnrollmentProfiles : SMS_BaseClass
{
    String ConfigurationUrl;
    DateTime CreationTime;
    String Department;
    String Description;
    UInt32 DeviceCount;
    UInt32 EnrollmentProgram;
    UInt32 IsDefault;
    UInt32 IsUserChallenge;
    DateTime ModifiedTime;
    String Name;
    UInt32 PlatformType;
    String ProfileId;
    String ProfileSettings;
    UInt32 SupervisionMode;
};

```

## Methods

The `SMS_MDMCorpEnrollmentProfiles` class does not define any methods.

## Properties

`ConfigurationUrl` Data type: `String`

Access type: Read/Write

Qualifiers: none

The configuration URL used for enrollment.

`CreationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time the enrollment profile was created.

`Department` Data type: `String`

Access type: Read/Write

Qualifiers: none

Department.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the enrollment profile.

`DeviceCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of devices associated with the profile.

`EnrollmentProgram` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Enrollment Program.

`IsDefault` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Is the enrollment profile the default.

`IsUserChallenge` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Profile is user challenged.

`ModifiedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time the enrollment profile was modified.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the enrollment profile.

`PlatformType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Platform Type.

`ProfileId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Enrollment profile ID.

`ProfileSettings` Data type: `String`

Access type: Read/Write

Qualifiers: none

The enrollment profile settings.

`SupervisionMode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Profile mode is supervised or not supervised for iOS.

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