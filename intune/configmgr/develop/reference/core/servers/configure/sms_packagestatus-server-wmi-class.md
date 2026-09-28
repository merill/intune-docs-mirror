---
layout: Conceptual
title: SMS_PackageStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatus-server-wmi-class
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
description: Learn how to provide a summary report of the health of packages and distribution points in the site within Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c6acdc8a-e033-ee7b-c697-9e295ab8538d
document_version_independent_id: 5378b831-4628-3f61-4416-f868ade2a217
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: d4674461-7773-3d11-909a-0fe2a012cf81
---

# SMS_PackageStatus Class - Configuration Manager | Microsoft Learn

The `SMS_PackageStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a summary report of the health of packages and distribution points in the site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageStatus : SMS_BaseClass
{
      String Location;
      String PackageID;
      SInt32 Personality;
      String PkgServer;
      String ShareName;
      String SiteCode;
      SInt32 Status;
      SInt32 Type;
      DateTime UpdateTime;
};
```

## Methods

The `SMS_PackageStatus` class does not define any methods.

## Properties

`Location` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Universal Naming Convention (UNC) path or network abstraction layer (NAL) path to where the package is stored or distributed.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The unique local ID for the package.

`Personality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, enumeration]

Status personality. Possible values are:

| Value | Personality |
| --- | --- |
| 0 | NONE |
| 1 | MAC |
| 2 | FPNW |

`PkgServer` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

If `Type` is MASTER (1), is the compressed copy of the package on the site server. If `Type` is COPY (2), `PkgServer` is the distribution point.

`ShareName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The share to which the package was distributed.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The site code for the site.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, enumeration]

Status. Possible values are:

| Value | Status |
| --- | --- |
| 0 | NONE |
| 1 | SENT |
| 2 | RECEIVED |
| 3 | INSTALLED |
| 4 | RETRY |
| 5 | FAILED |
| 6 | REMOVED |
| 7 | PENDING\_REMOVE |

`Type` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, enumeration]

The status type. Possible values are:

| Value | Status type |
| --- | --- |
| 1 | MASTER |
| 2 | COPY |

`UpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

When `Type` is MASTER (1), the time when the compressed copy was created or merged. When `Type` is COPY (2), `UpdateTime` is the time when the distribution point was updated.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class is used internally by the server Distribution Manager component and is not used directly to produce any of the package status information that you see in the Configuration Manager console.

    You can distribute multiple packages concurrently to multiple destinations. `SMS_PackageStatus` allows monitoring when packages arrive at distribution points. All the displayed dates are based on the time zone in which the Configuration Manager console is running.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).