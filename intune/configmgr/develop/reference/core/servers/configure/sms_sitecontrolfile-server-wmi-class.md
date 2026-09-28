---
layout: Conceptual
title: SMS_SiteControlFile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class
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
description: Learn how to use the SMS_SiteControlFile class which represents the site control file and methods to maintain version control of the site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3a2908f7-3d41-3061-0572-8fe6789228ab
document_version_independent_id: 1e68c796-2ffe-eb7e-1029-f78098852285
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: baff6cf7-5adf-ecf1-0e90-57e2f7378cc9
---

# SMS_SiteControlFile Class - Configuration Manager | Microsoft Learn

The `SMS_SiteControlFile` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the site control file and contains methods to maintain version control of the site control file.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteControlFile : SMS_BaseClass
{
     String BuildNumber;
     UInt32 FileType;
     String FormatVersion;
     String SCFData;
     UInt32 SerialNumber;
     String SiteCode;
};
```

## Methods

The `SMS_SiteControlFile` class does not define any methods.

## Properties

`BuildNumber` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Build number of the Configuration Manager installation that creates the site control file. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

This property is deprecated.

`FormatVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Version of the site control file format. The default value is "".

`SCFData` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy, large]

Current site control file data in text format (accumulated deltas).

`SerialNumber` Data type: `UInt32`

Access type: ReadWrite

Qualifiers: [key]

Unique ID of the file itself. The number is incremented every time the file changes. The default value is 0.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [key, read, SizeLimit("3")]

Site code of the site associated with the site control file. The default value is "".

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Your application uses the methods of this class to perform version control of the site control file. To update the contents of the site control file, the application should use classes derived from [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).