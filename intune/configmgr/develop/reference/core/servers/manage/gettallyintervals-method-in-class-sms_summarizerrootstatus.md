---
layout: Conceptual
title: GetTallyIntervals Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/gettallyintervals-method-in-class-sms_summarizerrootstatus
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
description: Learn how to use the GetTallyIntervals method to get an array of tally intervals and the default interval.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 18d3a06a-7183-a2e0-65a1-14cff2c7e195
document_version_independent_id: e8da4700-8e2a-196b-3ac5-7fe6e9e1d04b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/gettallyintervals-method-in-class-sms_summarizerrootstatus.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/gettallyintervals-method-in-class-sms_summarizerrootstatus
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/gettallyintervals-method-in-class-sms_summarizerrootstatus.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 940ee899-442a-615f-a210-43e785f75b04
---

# GetTallyIntervals Method - Configuration Manager | Microsoft Learn

The `GetTallyIntervals` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets an array of tally intervals and the default interval.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetTallyIntervals(
   String SiteCode,
    String ComponentName,
    String TallyIntervals[],
    String DefaultInterval
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: [in, SizeLimit("3")]

The site code of the site for which the status is reported.

`ComponentName` Data type: `String`

Qualifiers: [in, SizeLimit("3")]

The name of the component.

`TallyIntervals` Data type: `String` Array

Qualifiers: [out]

The tally intervals.

`DefaultInterval` Data type: `String`

Qualifiers: [out]

The default interval.

## Return Values

An `SInt32` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).