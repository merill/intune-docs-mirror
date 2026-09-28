---
layout: Conceptual
title: SMS_PackageStatusDistPointsSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class
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
description: The SMS_PackageStatusDistPointsSummarizer WMI class is an SMS Provider server class, in Configuration Manager, that lists the distribution summary for packages a given distribution point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1248c4ac-ca76-5a47-1628-5b3d1e7dae0c
document_version_independent_id: 5525a826-0349-7956-43fe-6aff67485577
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dfd8bd37-238e-f4a9-b74e-90ce6adffd51
---

# SMS_PackageStatusDistPointsSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_PackageStatusDistPointsSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists the distribution summary for packages on given site for a given distribution point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageStatusDistPointsSummarizer : SMS_BaseClass
{
      DateTime LastCopied;
      String PackageID;
      UInt32 PackageType;
      UInt32 SecuredTypeID;
      String SecureObjectID;
      String ServerNALPath;
      String SiteCode;
      String SourceNALPath;
      UInt32 SourceVersion;
      UInt32 State;
      DateTime SummaryDate;
};
```

## Methods

The `SMS_PackageStatusDistPointsSummarizer` class does not define any methods.

## Properties

`LastCopied` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC), when the package source files were last successfully copied to the distribution point.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("8")]

Configuration Manager-assigned ID for the package.

`PackageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

The type of package.

| Value | Description |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 7 | PKG\_TYPE\_VIRTUAL\_APP |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |

`SecuredTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Secured type of related package.

`SecureObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Secure object ID. For app, it is model name. For others, it is package ID.

`ServerNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Network abstraction layer (NAL) path to the distribution point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

Site code of the site.

`SourceNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

NAL path to the package source files.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Package source version number currently installed on this distribution point.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [ENUMERATION]

The state of the source files on the distribution point. Possible values are:

| Value | State |
| --- | --- |
| 0 | INSTALLED |
| 1 | INSTALL\_PENDING |
| 2 | INSTALL\_RETRYING |
| 3 | INSTALL\_FAILED |
| 4 | REMOVAL\_PENDING |
| 5 | REMOVAL\_RETRYING |
| 6 | REMOVAL\_FAILED |
| 7 | CONTENT\_UPDATING |
| 8 | CONTENT\_MONITORING |

`SummaryDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC), when a change in package status for the sites was most recently reported.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).