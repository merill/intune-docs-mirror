---
layout: Conceptual
title: TestSmtpConnection Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/testsmtpconnection-method-in-class-sms_subscription
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
description: A Windows Management Instrumentation class method that tests the SMTP connection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a5b0308c-72f2-1f61-b920-c172d1a26266
document_version_independent_id: c2f7d771-be02-6d59-127e-191416a1905a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/testsmtpconnection-method-in-class-sms_subscription.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/testsmtpconnection-method-in-class-sms_subscription
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/testsmtpconnection-method-in-class-sms_subscription.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e673420-7ed3-d2a3-c8c5-e77ddcaa2921
---

# TestSmtpConnection Method - Configuration Manager | Microsoft Learn

The `TestSmtpConnection` Windows Management Instrumentation (WMI) class method, in Configuration Manager, tests the SMTP connection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 TestSmtpConnection(
     String ServerFqdn,
     UInt32 Port,
     String Sender,
     String Recipients,
     UInt32 AuthenticationType,
     String UserName,
     String EncryptPassword,
     UInt32 TestID
);
```

#### Parameters

`ServerFqdn` Data type: `String`

Qualifiers: `[in]`

The FQDN of the SMTP server.

`Port` Data type: `UInt32`

Qualifiers: `[in]`

The port for the SMTP server.

`Sender` Data type: `String`

Qualifiers: `[in]`

Email address of the sender.

`Recipients` Data type: `String`

Qualifiers: `[in]`

Email addresses of the recipients.

`AuthenticationType` Data type: `UInt32`

Qualifiers: `[in]`

Authentication type. Possible values are:

| Value | Authentication type |
| --- | --- |
| 0 | Anonymous access. |
| 1 | Use the computer account of the site server. |
| 2 | Use the specified user name and password. |

`UserName` Data type: `String`

Qualifiers: `[in]`

User name of the SMTP server connection account. This is used when `AuthenticationType` is 2.

`EncryptPassword` Data type: `String`

Qualifiers: `[in]`

The encrypted password for the SMTP server connection account. This is used when `AuthenticationType` is 2.

`TestID` Data type: `UInt32`

Qualifiers: `[out]`

Test identifier. Used by `GetTestSmtpConnectionResult` to the test result.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).