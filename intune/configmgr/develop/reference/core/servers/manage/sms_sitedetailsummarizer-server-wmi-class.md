---
layout: Conceptual
title: SMS_SiteDetailSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class
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
description: Article detailing the use of SMS_SiteDetailSummarizer to provide per-site status of components and the system.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 41d0ec29-d515-8745-7593-c3e50ab7ad28
document_version_independent_id: 3c4ba058-a110-52fd-638c-86d23520d413
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c19276bf-134f-79c9-9eab-09d4396bf8c1
---

# SMS_SiteDetailSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_SiteDetailSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides per-site status of components and the system. An instance of this class is created for each site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteDetailSummarizer : SMS_BaseClass
{
      UInt32 AvailabilityState;
      UInt32 DatabaseFree;
      UInt32 Errors;
      UInt32 Infos;
      String SiteCode;
      String SiteName;
      UInt32 Status;
      String TallyInterval;
      UInt32 TransFree;
      String Version;
      UInt32 Warnings;
};
```

## Methods

The `SMS_SiteDetailSummarizer` class does not define any methods.

## Properties

`AvailabilityState` Data type: `UInt32`

Access type: Read

Qualifiers: None

Availability state of the site. The default value is 0.

`DatabaseFree` Data type: `UInt32`

Access type: Read

Qualifiers: None

Percentage of free storage space available for the site databases.

`Errors` Data type: `UInt32`

Access type: Read

Qualifiers: None

Total number of error status messages reported by all server components in this site during the tally interval.

`Infos` Data type: `UInt32`

Access type: Read

Qualifiers: None

Total number of informational status messages reported by all server components in this site during the tally interval.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key, SizeLimit("3")]

Site code of a Configuration Manager site.

`SiteName` Data type: `String`

Access type: Read

Qualifiers: None

Friendly name of the site.

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: [ToInstance]

Status value indicating the health of the component. Possible values are:

| Value | Status |
| --- | --- |
| GREEN(0) | OK. There are no warning or error messages. |
| YELLOW(1) | Warning. Warning messages were generated, but error messages were not generated. |
| RED(2) | Critical. There are error messages. |

`TallyInterval` Data type: `String`

Access type: Read

Qualifiers: [key]

Interval for which the detailed statistics apply. You must specify a tally interval in your WHERE clause to query instances of this class. The statistics are reset to zero each time the schedule elapses. To use this property, see How To Read Tally Intervals.

`TransFree` Data type: `UInt32`

Access type: Read

Qualifiers: None

Percentage of free storage space available for the transaction logs of the site databases.

`Version` Data type: `String`

Access type: Read

Qualifiers: None

Version of Configuration Manager that is installed on the site, including the service pack if one is installed.

`Warnings` Data type: `UInt32`

Access type: Read

Qualifiers: None

Total number of warning status messages reported by all server components in this site during the tally interval.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class summarizes all informational, warning, and error messages for the site. An instance of the class is created for each server component that is running in the site.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).