---
layout: Conceptual
title: SMS_SummarizerSiteStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class
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
description: Learn how to use the SMS_SummarizerSiteStatus class to represent summarizer for the overall health of each site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7bdc946d-019a-4623-1aa2-f267ac7146aa
document_version_independent_id: f415255a-229f-c75a-c7dd-4ce98353670e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c73275b-d8ec-a7d5-0622-cdfb23642558
---

# SMS_SummarizerSiteStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SummarizerSiteStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a summarizer for the overall health of each site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizerSiteStatus : SMS_BaseClass
{
     String SiteCode;
    UInt32 Status;
};
```

## Methods

The `SMS_SummarizerSiteStatus` class doesn't define any methods.

## Properties

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key]

Site code of the Configuration Manager site.

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating the overall health of the site. Possible values are listed below. Determining the overall status for the site hierarchy is based on the status of Configuration Manager components and storage objects.

| Value | Status |
| --- | --- |
| GREEN(0) | OK. There are no warning or error messages. |
| YELLOW(1) | Warning. Warning messages were generated, but error messages weren't generated. This status also indicates that the storage objects are approaching their threshold. |
| RED(2) | Critical. There are error messages, or the storage objects have exceeded their thresholds. |

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).