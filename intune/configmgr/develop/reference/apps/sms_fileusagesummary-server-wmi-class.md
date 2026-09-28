---
layout: Conceptual
title: SMS_FileUsageSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn about the simplified syntax, methods, properties and requirements of the SMS_FileUsageSummary server class.
locale: en-us
document_id: f9ecce08-001a-e2c6-0715-a5f5e1f60f00
document_version_independent_id: fd7056ff-6fe2-8f78-cd99-1dcdba369e55
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 58091c59-178c-06b2-5466-d9a8857e3a8f
---

# SMS_FileUsageSummary Class - Configuration Manager | Microsoft Learn

The `SMS_FileUsageSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides a usage summary of a metered file.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_FileUsageSummary : SMS_BaseClass
{
      UInt32 DistinctUserCount;
      SInt64 FileID;
      DateTime IntervalStart;
      UInt32 IntervalWidth;
      String SiteCode;
};
```

## Methods

The `SMS_FileUsageSummary` class does not define any methods.

## Properties

`DistinctUserCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Count of the distinct number of users who used the file during the summarization interval.

`FileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: [key]

File ID of the summarized file. To find the file information, match `FileID` with the ID in [SMS_ProductFileInfo Server WMI Class](sms_productfileinfo-server-wmi-class). To find the rules that caused the file to be metered, match `FileID` to the ID in [SMS_MeteredFiles Server WMI Class](sms_meteredfiles-server-wmi-class).

`IntervalStart` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [key]

Start time of the summarization interval.

`IntervalWidth` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Size of the summarization interval, in minutes. Possible values are 15 and 60.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Site code for the clients that used the file during the summarization interval. This identifies the site that originally generated the summary.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class counts the number of distinct users and computers that used a metered file during a particular interval on a particular site.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).