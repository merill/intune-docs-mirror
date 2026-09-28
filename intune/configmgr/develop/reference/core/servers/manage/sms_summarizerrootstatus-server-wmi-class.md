---
layout: Conceptual
title: SMS_SummarizerRootStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class
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
description: In Configuration Manager, the SMS_SummarizerRootStatus Windows Management Instrumentation class is an SMS Provider server class that represents a summarizer for the overall health of the entire site hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2fe7e9e6-4630-0976-d40a-ff07e68dfa72
document_version_independent_id: 75d1a07e-18d2-4a53-10f9-6137fa88ef90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e6f840d-c248-21fe-bff3-58fdc88a57b7
---

# SMS_SummarizerRootStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SummarizerRootStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a summarizer for the overall health of the entire site hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizerRootStatus : SMS_BaseClass
{
    UInt32 Status;
};
```

## Methods

The following table shows the methods in `SMS_SummarizerRootStatus`.

| Method | Description |
| --- | --- |
| [GetTallyIntervals Method in Class SMS_SummarizerRootStatus](gettallyintervals-method-in-class-sms_summarizerrootstatus) | Gets an array of tally intervals and the default interval. |

## Properties

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

Value indicating the overall health of the site hierarchy. Possible values are listed below. Determining the overall status for the site hierarchy is based on the status of the child sites.

| Value | Properties |
| --- | --- |
| GREEN(0) | OK. All the child sites reported a GREEN status. |
| YELLOW(1) | Warning. One or more child sites reported a YELLOW status, but no RED status was reported by a child site. |
| RED(2) | Critical. One or more of the child sites reported a RED status. |

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).