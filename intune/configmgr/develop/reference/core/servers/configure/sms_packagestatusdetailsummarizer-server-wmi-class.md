---
layout: Conceptual
title: SMS_PackageStatusDetailSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class
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
description: In Configuration Manager, the SMS_PackageStatusDetailSummarizer Windows Management Instrumentation class is an SMS Provider server class that lists the distribution summary for a given package for a given site in a hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ee2cf5b5-3fff-6bf9-ee1d-1c2c8fb843f3
document_version_independent_id: 5516318f-0157-017e-05eb-258f3a761f97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c457ab38-7b40-d1ed-4383-663460c169a7
---

# SMS_PackageStatusDetailSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_PackageStatusDetailSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists the distribution summary for a given package for a given site in a hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageStatusDetailSummarizer : SMS_BaseClass
{
      UInt32 Failed;
      UInt32 Installed;
      String Name;
      String PackageID;
      UInt32 Retrying;
      String SiteCode;
      String SiteName;
      UInt32 SourceVersion;
      DateTime SummaryDate;
      UInt32 Targeted;
};
```

## Methods

The `SMS_PackageStatusDetailSummarizer` class does not define any methods.

## Properties

`Failed` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points in the site that have exceeded the number of retries allowed during an installation or removal operation and that are currently in a state of installation-failed or retry-failed.

`Installed` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points in the site that have successfully installed the current source version of the package.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name assigned to the package.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [ key, SizeLimit("8")]

ID assigned by Configuration Manager for the package.

`Retrying` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points in the site that have had at least one failure during an installation or removal operation but have not yet exceeded the number of retries allowed and are currently in a state of installation-retrying or removal-retrying.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

Site code for each site that has at least one distribution point specified for the package.

`SiteName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Friendly display name for the site.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Version of the package source files.

`SummaryDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time, in Universal Coordinated Time (UTC) when a change in package status for this site was most recently reported.

`Targeted` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The total number of distribution points in the site that are targeted for the package.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).