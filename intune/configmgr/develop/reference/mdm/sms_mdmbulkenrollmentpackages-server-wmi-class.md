---
layout: Conceptual
title: SMS_MDMBulkEnrollmentPackages Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentpackages-server-wmi-class
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
description: The SMS_MDMBulkEnrollmentPackages WMI class is an SMS Provider server class that represents on-premises Mobile Device Management bulk enrollment packages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ae61d7d9-0639-a768-3066-9b950b0df481
document_version_independent_id: 162d13ab-fa64-55af-fee3-044e3cdcc53e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentpackages-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmbulkenrollmentpackages-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentpackages-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 355e114c-2f2d-5a84-ca35-56f02e50bc03
---

# SMS_MDMBulkEnrollmentPackages Class - Configuration Manager | Microsoft Learn

The `SMS_MDMBulkEnrollmentPackages` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) bulk enrollment packages.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMBulkEnrollmentPackages : SMS_BaseClass
{
    String CertificateId;
    DateTime CreationTime;
    DateTime ExpiryTime;
    UInt32 Package_ID;
    String PackageName;
    UInt32 Profile_ID;
    String  Profile_UniqueID;
    String ProfileName;
    UInt32 State;
};

```

## Methods

The following table lists the methods in the `SMS_MDMBulkEnrollmentPackages` class.

| Method | Description |
| --- | --- |
| [ImportForProfile Method in Class SMS_MDMBulkEnrollmentPackages](importforprofile-method-in-class-sms_mdmbulkenrollmentpackages) | Imports an MDM bulk enrollment package for a profile. |

## Properties

`CertificateId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique certificate ID, as a GUID.

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time the package was created.

`ExpiryTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time the package expires.

`Package_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Package ID.

`PackageName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package name.

`Profile_ID` Data type: `uint32`

Access type: Read/Write

Qualifiers: [key]

Profile ID.

`Profile_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, not\_null]

Unique ID of the Profile.

`ProfileName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Profile name.

`State` Data type: `uint32`

Access type: Read/Write

Qualifiers: none

State of the package.

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