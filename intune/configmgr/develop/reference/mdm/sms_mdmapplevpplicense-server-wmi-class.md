---
layout: Conceptual
title: SMS_MDMAppleVppLicense Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmapplevpplicense-server-wmi-class
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
description: The SMS_MDMAppleVppLicense WMI class represents an Apple Volume Purchase Program (VPP) licensed application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2ee22da0-528a-94c2-b570-2acb2c2f2d31
document_version_independent_id: b2bc3bb8-5ef4-b671-c812-025a74933454
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmapplevpplicense-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmapplevpplicense-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmapplevpplicense-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8b1867e8-07cb-0dde-ba6d-091b07156522
---

# SMS_MDMAppleVppLicense Class - Configuration Manager | Microsoft Learn

The `SMS_MDMAppleVppLicense` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an Apple Volume Purchase Program (VPP) licensed application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMAppleVppLicense : SMS_BaseClass
{
    String ApplicationID;
    UInt32 AvailableLicenses;
    String BundleID;
    String DeepLinkUrl;
    String InfoLink;
    DateTime LastUpdateTime;
    String Publisher;
    DateTime ReleaseDate;
    String SupportedDevices;
    String Title;
    UInt32 TotalLicenses;
    String Version;
};

```

## Methods

The `SMS_MDMAppleVppLicense` class does not define any methods.

## Properties

`ApplicationID` Data type: `String`

Access type: Read

Qualifiers: [key]

The AppleID of the application.

`AvailableLicenses` Data type: `UInt32`

Access type: Read

Qualifiers: none

Current number of available licenses for the application.

`BundleID` Data type: `String`

Access type: Read

Qualifiers: none

Apple App Store bundle ID.

`DeepLinkUrl` Data type: `String`

Access type: Read

Qualifiers: none

The application VPP link in the Apple App Store.

`InfoLink` Data type: `String`

Access type: Read

Qualifiers: none

The link to the application in the Apple App Store.

`LastUpdateTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The last time the VPP license data for the application was updated.

`Publisher` Data type: `String`

Access type: Read

Qualifiers: none

Publisher of the application in the Apple App Store.

`ReleaseDate` Data type: `DateTime`

Access type: Read

Qualifiers: none

The application's release date to the Apple App Store.

`SupportedDevices` Data type: `String`

Access type: Read

Qualifiers: none

The devices supported by the application.

`Title` Data type: `String`

Access type: Read

Qualifiers: none

Title of the application in Apple App Store.

`TotalLicenses` Data type: `UInt32`

Access type: Read

Qualifiers: none

Total number of licenses for the application.

`Version` Data type: `String`

Access type: Read

Qualifiers: none

Application version in the Apple App Store.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).