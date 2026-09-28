---
layout: Conceptual
title: GetTestSmtpConnectionResult Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/gettestsmtpconnectionresult-method-in-class-sms_subscription
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
description: Learn how the GetTestSmtpConnectionResult Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the test SMTP connection result.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c3cf128d-1070-24de-260b-167457425ed9
document_version_independent_id: 2bcc6b75-0f0c-91ec-0127-591ac3ffe879
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/gettestsmtpconnectionresult-method-in-class-sms_subscription.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/gettestsmtpconnectionresult-method-in-class-sms_subscription
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/gettestsmtpconnectionresult-method-in-class-sms_subscription.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9263f422-6598-3332-7859-7537ee1fa1b1
---

# GetTestSmtpConnectionResult Method - Configuration Manager | Microsoft Learn

The `GetTestSmtpConnectionResult` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the test SMTP connection result.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 GetTestSmtpConnectionResult(
     UInt32 TestID,
     UInt32 ErrorCode
);
```

#### Parameters

`TestID` Data type: `UInt32`

Qualifiers: `[in]`

Test identifier returned by `TestSmtpConnection`.

`ErrorCode` Data type: `UInt32`

Qualifiers: `[out]`

Represents the test results. Possible values are:

| Value | Error code |
| --- | --- |
| 0 | Success. |
| 1 | The test is initializing. |
| 2 | Email address formatting error. |
| 3 | Failed recipients error. |
| 4 | Connection error. |
| 5 | Other error. |
| 6 | Operation timed out. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).