---
layout: Conceptual
title: SMS_CH_EvalResult Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_ch_evalresult-server-wmi-class
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
description: The SMS_CH_EvalResult Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents client evaluation results.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c5d9ef6c-03c5-e29e-d759-74105e24b0ab
document_version_independent_id: a694fc7e-eddb-c50c-7906-32c0914f4100
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/sms_ch_evalresult-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/sms_ch_evalresult-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/sms_ch_evalresult-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 26c5d730-68e0-1fb5-e5cb-1d89ff12ccf8
---

# SMS_CH_EvalResult Class - Configuration Manager | Microsoft Learn

The `SMS_CH_EvalResult` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents client evaluation results.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CH_EvalResult : SMS_BaseClass
{
    DateTime EvalTime;
    String HealthCheckDescription;
    String HealthCheckGUID;
    UInt32 ResourceID;
    UInt32 Result;
    UInt32 ResultCode;
    String ResultDetail;
    UInt32 ResultType;
};
```

## Methods

The `SMS_CH_EvalResult` class does not define any methods.

## Properties

`EvalTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Evaluation time.

`HealthCheckDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Health Check description.

`HealthCheckGUID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Health check GUID.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Unique Configuration Manager-supplied ID for the resource.

`Result` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Evaluation result.

`ResultCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Result code.

`ResultDetail` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Result detail.

`ResultType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Result type.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).