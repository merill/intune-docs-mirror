---
layout: Conceptual
title: SMS_Identification Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class
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
description: The SMS_Identification Windows Management Instrumentation (WMI) class is an SMS Provider server class that provides basic information about the installed SMS_Site Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1c3bbfd0-c010-5d2f-56b4-380244b3d911
document_version_independent_id: e2522fd3-a030-769e-96f5-cf9864547f64
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 52ff3578-b357-ebca-bb13-b2de5038cd7b
---

# SMS_Identification Class - Configuration Manager | Microsoft Learn

The `SMS_Identification` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides basic information about the installed [SMS_Site Server WMI Class](sms_site-server-wmi-class) object, for example, its language version, site code, and provider. This class should return only one instance.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Identification : SMS_BaseClass
{
     UInt32 License;
     UInt32 LocaleID;
     UInt32 MonthlyReleaseVersion;
     UInt32 Reserved;
     String ServiceAccountName;
     String SMSAvailableConsoleVersion;
     UInt32 SMSBuildNumber;
     UInt32 SMSMinBuildNumber;
     String SMSProviderServer;
     String SMSSiteServer;
     String SMSVersion;
     String ThisSiteCode;
     String ThisSiteName;
     String UIManifestHash;
     String UIManifestHashAlgorithm;
     String UIUpdateManifestHash;
     String UIUpdateManifestHashAlgorithm;
};
```

## Methods

The following table lists the methods in `SMS_Identification`.

| Method | Description |
| --- | --- |
| [GetCurrentUser Method in Class SMS_Identification](getcurrentuser-method-in-class-sms_identification) | Gets the domain\user name being used by the SMS Provider for authentication. |
| [GetFileBinary Method in Class SMS_Identification](getfilebinary-method-in-class-sms_identification) | Gets the binary user interface for a feature. |
| [GetProviderVersion Method in Class SMS_Identification](getproviderversion-method-in-class-sms_identification) | Gets the product version string from the version resources of the SMS Provider DLL. |
| [GetSiteID Method in Class SMS_Identification](getsiteid-method-in-class-sms_identification) | Gets the unique ID of the installed Configuration Manager site. |

## Properties

`License` Data type: `UInt32`

Access type: Read

Qualifiers: none

License type of the installation. Possible values are:

| Value | License type |
| --- | --- |
| 0 | Evaluation |
| 1 | Non-evaluation |

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Subtype("Locale Id")]

ID of the locale used by the Configuration Manager installation, for example, English (1033) or German (1031).

`MonthlyReleaseVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Monthly Configuration Manager release version.

`Reserved` Data type: `UInt32`

Access type: Read

Qualifiers: none

For internal use only.

`ServiceAccountName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the Configuration Manager service account, which is a special user account having administrative privileges, that uses Configuration Manager to perform certain activities. The value includes the domain.

`SMSAvailableConsoleVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Available Configuration Manager console version.

`SMSBuildNumber` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Build version number of the installed Configuration Manager software.

`SMSMinBuildNumber` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`SMSProviderServer` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the server on which the SMS Provider is installed.

Note

If a site has multiple SMS Providers installed, this will just return one of them.

`SMSSiteServer` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the server on which the Configuration Manager site server components are installed.

`SMSVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Major version number of the Configuration Manager installation, for example, 2.0. For the complete version number, see the `Version` property of [SMS_Site Server WMI Class](sms_site-server-wmi-class).

`ThisSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Site code for the installation.

`ThisSiteName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Friendly name of the site.

`UIManifestHash` Data type: `String`

Access type: Read/Write

Qualifiers: None

Hash of the UIManifest.xml file stored on the site server.

`UIManifestHashAlgorithm` Data type: `String`

Access type: Read/Write

Qualifiers: None

Hash algorithm used to calculate the hash of the UIManifest.xml file stored on the site server.

`UIUpdateManifestHash` Data type: `String`

Access type: Read/Write

Qualifiers: None

Hash of the UIUpdatemanifest.xml file stored on the site server.

`UIUpdateManifestHashAlgorithm` Data type: `String`

Access type: Read/Write

Qualifiers: None

Hash algorithm used to calculate the hash of the UIUpdatemanifest.xml file stored on the site server.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).