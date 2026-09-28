---
layout: Conceptual
title: SMS_PackageStatusRootSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class
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
description: The SMS_PackageStatusRootSummarizer Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that lists the distribution summary for a given package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e18e5988-a404-ce5d-1eea-44ee63a95f39
document_version_independent_id: f3699713-ab90-5c73-242f-2f6f3f7e9c81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4ad74b31-f82f-e951-724d-abe057246aac
---

# SMS_PackageStatusRootSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_PackageStatusRootSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists the distribution summary for a given package for all sites in a hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageStatusRootSummarizer : SMS_BaseClass
{
      UInt32 Failed;
      UInt32 Installed;
      String Name;
      String PackageID;
      UInt32 Retrying;
      UInt32 SourceCompressedSize;
      DateTime SourceDate;
      String SourceSite;
      UInt32 SourceSize;
      UInt32 SourceVersion;
      UInt32 Targeted;
};
```

## Methods

The `SMS_PackageStatusRootSummarizer` class doesn't define any methods.

## Properties

`Failed` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points for this package that have exceeded the number of retries allowed during an installation or removal operation and that are currently in a state of installation-failed or retry-failed.

`Installed` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points that have successfully copied the current source version of the package. A distribution point is considered installed until an update, refresh, or removal operation is specified.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("64")]

Name of the package.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key,SizeLimit("8")]

Configuration Manager-assigned ID for the package.

`Retrying` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points for this package that have had at least one failure during an installation or removal operation but haven't yet exceeded the number of retries allowed and are currently in a state of installation-retrying or removal-retrying.

`SourceCompressedSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size, in kilobytes, of the compressed version of the package source files.

`SourceDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when this version of the source files was created.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

Site code of the site where the package originated.

`SourceSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size, in kilobytes, of the package source files.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Current version of the package source files, as defined by the originating site.

`Targeted` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total number of distribution points (including child sites) that are specified to have a copy of the package. A distribution point remains targeted until it's specified for removal.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).