---
layout: Conceptual
title: SMS_LicensedVppApps Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_licensedvppapps-server-wmi-class
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
description: The SMS_LicensedVppApps WMI class represents license Information for Apple App Store Volume Purchase Program (VPP) and Microsoft Store for Business applications.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ef67b608-5c75-1d1b-4245-efda02e9a027
document_version_independent_id: 72fda115-280b-86ac-36c7-d09776a851ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_licensedvppapps-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_licensedvppapps-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_licensedvppapps-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d984c28f-e9aa-1f3b-06dc-beaa03c36e7e
---

# SMS_LicensedVppApps Class - Configuration Manager | Microsoft Learn

The `SMS_LicensedVppApps` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents license Information for Apple App Store Volume Purchase Program (VPP) and Microsoft Store for Business applications.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_LicensedVppApps : SMS_BaseClass
{
    String ApproximateSize;
    String ApplicationID;
    String ApplicationMetadata;
    SInt32 AvailableLicenses;
    DateTime ContentLastModified;
    DateTime CreatedDate;
    String DisplayName;
    DateTime LastSuccessfulSync;
    DateTime LastSync;
    UInt32 LicenseType;
    UInt32 Platform;
    String Publisher;
    String SoftwareVersion;
    String StoreCategory;
    String StoreLink;
    String SupportedLanguages;
    String SupportedProcessors;
    SInt32 TotalLicenses;
};

```

## Methods

The `SMS_LicensedVppApps` class does not define any methods.

## Properties

`ApproximateSize` Data type: `String`

Access type: Read

Qualifiers: none

The approximate size of the application.

`ApplicationID` Data type: `String`

Access type: Read

Qualifiers: [key]

The ID of the application.

`ApplicationMetadata` Data type: `String`

Access type: Read

Qualifiers: [lazy]

The application metadata.

`AvailableLicenses` Data type: `SInt32`

Access type: Read

Qualifiers: none

The number of available licenses for the application.

`ContentLastModified` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date and time that the content was last modified.

`CreatedDate` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date the application was created.

`DisplayName` Data type: `String`

Access type: Read

Qualifiers: none

The display name of the application.

`LastSuccessfulSync` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date and time of the last successful synchronization.

`LastSync` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date and time of the last synchronization.

`LicenseType` Data type: `UInt32`

Access type: Read

Qualifiers: none

The type of license. Possible values are:

| Value | License type |
| --- | --- |
| 0 | Online |
| 1 | Offline |

`Platform` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The platform on which the application runs. Possible values are:

| Value | Platform |
| --- | --- |
| 0 or 1 | Windows |
| 2 | iOS |

`Publisher` Data type: `String`

Access type: Read

Qualifiers: none

The name of the publisher of the application.

`SoftwareVersion` Data type: `String`

Access type: Read

Qualifiers: none

The application version.

`StoreCategory` Data type: `String`

Access type: Read

Qualifiers: none

The category of the application in the store.

`StoreLink` Data type: `String`

Access type: Read

Qualifiers: none

The link to the application in the store.

`SupportedLanguages` Data type: `String`

Access type: Read

Qualifiers: none

The languages the application supports.

`SupportedProcessors` Data type: `String`

Access type: Read

Qualifiers: none

The processor architectures that the application supports.

`TotalLicenses` Data type: `SInt32`

Access type: Read

Qualifiers: none

The total number of licenses for the application. -1 indicates unlimited licenses.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).