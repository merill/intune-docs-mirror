---
layout: Conceptual
title: SMS_BulkEnrollmentProfiles Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_bulkenrollmentprofiles-server-wmi-class
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
description: The  SMS_BulkEnrollmentProfiles Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents bulk enrollment profiles for Windows Embedded handheld devices.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d5b47d2d-5fd5-4d63-b98e-1bc9ac0feae2
document_version_independent_id: fb76e0a6-8095-32c8-8941-b20e9d175cb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_bulkenrollmentprofiles-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_bulkenrollmentprofiles-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_bulkenrollmentprofiles-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ea6e648c-cf2a-a3c4-2ca1-94d1b4ab5258
---

# SMS_BulkEnrollmentProfiles Class - Configuration Manager | Microsoft Learn

The `SMS_BulkEnrollmentProfiles` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents bulk enrollment profiles for Windows Embedded handheld devices.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BulkEnrollmentProfiles : SMS_BaseClass
{
    String Certificate_CI_UniqueID[];
    UInt32 EnrollmentProxyPointType;
    String EnrollProxyPointServerNames[];
    DateTime ExpirationDate;
    String FriendlyNamePrefix;
    UInt32 ID;
    Boolean IsEnabled;
    String ProfileDescription;
    UInt32 ProfileID;
    String ProfileName;
    UInt32 ProxyPort;
    String ProxyServer;
    String Thumbprint;
    String UserName;
    String Wifi_CI_UniqueID;
};

```

## Methods

The following table lists the methods in the `SMS_BulkEnrollmentProfiles` class.

| Method | Description |
| --- | --- |
| [GenerateProvisioningXML Method in Class SMS_BulkEnrollmentProfiles](generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles) | Generates provisioning data in XML format. |

## Properties

`Certificate_CI_UniqueID` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The unique ID for a certificate configuration item.

`EnrollmentProxyPointType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Specifies the type of URL for all enrollment proxy points. Possible values are:

| Value | Enrollment Proxy Point type |
| --- | --- |
| 0 | NONE |
| 1 | INTERNET |
| 2 | INTRANET |

`EnrollProxyPointServerNames` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The name of the enrollment proxy point server.

`ExpirationDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The expiration date of the certificate.

`FriendlyNamePrefix` Data type: `String`

Access type: Read/Write

Qualifiers: none

The friendly name prefix for the device.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

A unique profile ID.

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether the profile is enabled.

`ProfileDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

A description of the profile.

`ProfileID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The ID of the device enrollment profile.

`ProfileName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the device enrollment profile.

`ProxyPort` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The proxy port number.

`ProxyServer` Data type: `String`

Access type: Read/Write

Qualifiers: none

The proxy server.

`Thumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: none

The thumbprint of the certificate.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The user name.

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