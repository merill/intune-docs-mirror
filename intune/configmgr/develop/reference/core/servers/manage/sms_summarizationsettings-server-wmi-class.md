---
layout: Conceptual
title: SMS_SummarizationSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizationsettings-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents the site summarization settings for a site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5b51014d-367f-e527-dbba-17295bb4c52c
document_version_independent_id: 73aa7733-299c-54b7-f884-c49be6577b77
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_summarizationsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_summarizationsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_summarizationsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2a48fb15-4833-330b-7260-b6b9303a15e9
---

# SMS_SummarizationSettings Class - Configuration Manager | Microsoft Learn

The `SMS_SummarizationSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the site summarization settings for a site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizationSettings : SMS_BaseClass
{
    String ComponentName;
};
```

## Methods

The following table lists the methods in the `SMS_SummarizationSettings` class.

| Method | Description |
| --- | --- |
| [GetSummarizationSettings Method in Class SMS_SummarizationSettings](getsummarizationsettings-method-in-class-sms_summarizationsettings) | Gets the summarization schedule. |
| [SetSummarizationSettings Method in Class SMS_SummarizationSettings](setsummarizationsettings-method-in-class-sms_summarizationsettings) | Sets the summarization schedule. |

## Properties

`ComponentName` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null, read]

Name of the Configuration Manager component.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).