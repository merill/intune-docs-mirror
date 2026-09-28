---
layout: Conceptual
title: SMS_SiteSystemSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class
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
description: Learn how to represent a site system summarizer using the SMS_SiteSystemSummarizer class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2e66276c-a347-4e7a-9d05-6593a550411f
document_version_independent_id: 414aa3af-0cae-8fad-598f-7e2947959909
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4f2031af-1b4a-8488-c616-0bb59d9299b9
---

# SMS_SiteSystemSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_SiteSystemSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a site system summarizer. The site system summarizer reports physical system health data for each system and each system role in the Configuration Manager site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteSystemSummarizer : SMS_BaseClass
{
      UInt32 AvailabilityState;
      SInt64 BytesFree;
      SInt64 BytesTotal;
      DateTime DownSince;
      UInt32 ObjectType;
      SInt32 PercentFree;
      String Role;
      String SiteCode;
      String SiteObject;
      String SiteSystem;
      UInt32 Status;
};
```

## Methods

The `SMS_SiteSystemSummarizer` class does not define any methods.

## Properties

`AvailabilityState` Data type: `UInt32`

Access type: Read

Qualifiers: None

Availability state of the site system. The default value is 0.

`BytesFree` Data type: `SInt64`

Access type: Read

Qualifiers: None

Amount of free, unused storage space, in kilobytes, for the storage object.

`BytesTotal` Data type: `SInt64`

Access type: Read

Qualifiers: None

Maximum amount of storage space, in kilobytes, of the storage object. A negative value indicates that information is currently unavailable.

`DownSince` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time when the storage object was first found to be down (inaccessible). The storage object is considered down if the site server fails to connect to the storage object due to network problems, security problems, or other problems. The value is `null` if the storage object is accessible. The time zone is based on the time zone of the `SiteCode` property.

`ObjectType` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

Type of object for which the status is being reported. Possible values are:

| Value | Object type |
| --- | --- |
| 0 | NALPATH. A directory. |
| 1 | SQL\_DB. An SQL Server database. |
| 2 | SQL\_LOG. An SQL Server transaction log. |

`PercentFree` Data type: `SInt32`

Access type: Read

Qualifiers: None

Percentage of free storage space available on the storage object.

`Role` Data type: `String`

Access type: Read

Qualifiers: [key]

Configuration Manager role performed by the site system, for example:

- Distribution point
- SQL Server
- Software metering server
- Component server
- Site server

    `SiteCode` Data type: `String`

    Access type: Read

    Qualifiers: [key]

    Site code of Configuration Manager site.

    `SiteObject` Data type: `String`

    Access type: Read

    Qualifiers: [key]

    Network abstraction layer (NAL) path to a storage object that is one of the following:
- Directory that contains files
- Name of the database
- Transaction log

    `SiteSystem` Data type: `String`

    Access type: Read

    Qualifiers: [key]

    Name of the computer containing the storage object.

    `Status` Data type: `UInt32`

    Access type: Read

    Qualifiers: None

    Status value indicating the health of the component. Possible values are:

| Value | Status |
| --- | --- |
| GREEN(0) | OK. The storage objects are well below their thresholds. |
| YELLOW(1) | Warning. The storage objects are approaching their thresholds. |
| RED(2) | Critical. The storage objects have exceeded their thresholds. |

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    An instance of this class is created for every storage object used by Configuration Manager. Storage objects are defined by the `SiteObject` property.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).