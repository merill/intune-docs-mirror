---
layout: Conceptual
title: SMS_MDMBulkEnrollmentProfiles Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentprofiles-server-wmi-class
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
description: Learn how to represent On-premises Mobile Device Management (MDM) bulk enrollment profiles using SMS_BulkEnrollmentProfiles class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4150d1be-fc67-46e3-5bbd-ee9b4d6526e8
document_version_independent_id: 6e435706-805f-d2c3-c0c1-fcbabf0def9b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentprofiles-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmbulkenrollmentprofiles-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentprofiles-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5b005c94-5ece-1694-8f8f-d69961f4cf6b
---

# SMS_MDMBulkEnrollmentProfiles Class - Configuration Manager | Microsoft Learn

The `SMS_BulkEnrollmentProfiles` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) bulk enrollment profiles.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMBulkEnrollmentProfiles : SMS_BaseClass
{
    String Certificate_CI_UniqueID;
    Bool CRLCheckEnabled;
    UInt32 EnrolledDeviceCount;
    UInt32 EnrollmentProxyPointType;
    String EnrollmentProxyPointUrl;
    String MDMSiteCode
    UInt32 Profile_ID;
    String Profile_UniqueID;
    String ProfileDescription;
    String ProfileName;
    UInt32 ProfileType;
    UInt32 ProfileVersion;
    UInt32 ProxyPort;
    String ProxyServer;
    UInt32 Status;
    String Wifi_CI_UniqueID;
};

```

## Methods

The `SMS_MDMBulkEnrollmentProfiles` class does not define any methods.

## Properties

`Certificate_CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The unique ID for a certificate configuration item.

`CRLCheckEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if certificate revocation list (CRL) check is enabled.

`EnrolledDeviceCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of enrolled devices.

`EnrollmentProxyPointType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies the type of URL for all enrollment proxy points. Possible values are:

| Value | Enrollment Proxy Point type |
| --- | --- |
| 0 | NONE |
| 1 | INTERNET |
| 2 | INTRANET |

`EnrollmentProxyPointUrl` Data type: `String`

Access type: Read/Write

Qualifiers: none

Enrollment proxy point URL.

`MDMSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The MDM site code.

`Profile_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The profile ID.

`Profile_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, not\_null]

Unique ID of the profile.

`ProfileDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

The description of the profile.

`ProfileName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the profile.

`ProfileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The profile type.

`ProfileVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The version of the profile.

`ProxyPort` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The proxy port number.

`ProxyServer` Data type: `String`

Access type: Read/Write

Qualifiers: none

The proxy server.

`Status` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The status.

`Wifi_CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The unique ID for a Wi-Fi configuration item.

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