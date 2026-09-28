---
layout: Conceptual
title: SetSummarizationSettings Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/setsummarizationsettings-method-in-class-sms_summarizationsettings
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
description: In Configuration Manager, the SetSummarizationSettings WMI class method sets the summarization schedule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dbbcdf99-4723-e2b7-afe1-958f9b7f95f3
document_version_independent_id: 30d191bf-4c43-3098-4af9-fa54bf6002a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/setsummarizationsettings-method-in-class-sms_summarizationsettings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/setsummarizationsettings-method-in-class-sms_summarizationsettings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/setsummarizationsettings-method-in-class-sms_summarizationsettings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 92cc641b-037a-049d-112f-27cfc6537692
---

# SetSummarizationSettings Method - Configuration Manager | Microsoft Learn

In Configuration Manager, the `SetSummarizationSettings` Windows Management Instrumentation (WMI) class method sets the summarization schedule.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
sint32 SetSummarizationSettings(
     string SiteCode,
     uint32 SummarizationType,
     uint32 FirstIntervalMins,
     uint32 SecondIntervalMins,
     uint32 ThirdIntervalMins
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: `[in]`

The site code of the site associated with the summarization settings.

`SummarizationType` Data type: `UInt32`

Qualifiers: `[in]`

Types of summarization. Possible values are:

| Value | Summarization type |
| --- | --- |
| 2 | Application Deployment Summarization |
| 3 | Application State Summarization (spans all previous and current deployments) |

`FirstIntervalMins` Data type: `UInt32`

Qualifiers: `[out]`

The interval in minutes between summarizations for deployments that have a start date within 30 days (for deployment summarizations) or applications that have been created in the last 30 days (for application state summarization).

`SecondIntervalMins` Data type: `UInt32`

Qualifiers: `[out]`

The interval in minutes between summarizations for deployments that have a start date within the last 30-90 days (for deployment summarizations) or applications that have been created within the last 30-90 days (for application state summarization).

`ThirdIntervalMins` Data type: `UInt32`

Qualifiers: `[out]`

The interval in minutes between summarizations for deployments that have a start date over 90 days (for deployment summarizations) or applications that have been created over 90 days ago (for application state summarization).

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).