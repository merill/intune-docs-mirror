---
layout: Conceptual
title: GetCurrentUser Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getcurrentuser-method-in-class-sms_identification
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
description: Learn how to use the GetCurrentUser method to get the domain\user name that is used by the SMS Provider for authentication.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cf068298-133d-9324-6ce5-d0d6c5d23df5
document_version_independent_id: fd19f6b7-310b-6a8e-7e7b-9f696300342e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getcurrentuser-method-in-class-sms_identification.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getcurrentuser-method-in-class-sms_identification
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getcurrentuser-method-in-class-sms_identification.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 98531159-c18c-6f0b-8f5a-667d1ca0b08c
---

# GetCurrentUser Method - Configuration Manager | Microsoft Learn

The `GetCurrentUser` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the domain\user name that is used by the SMS Provider for authentication.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetCurrentUser(
     String UserName
);
```

#### Parameters

`UserName` Data type: `String`

Qualifiers: [out]

Domain\user name being used by the SMS Provider. This name might differ from the domain\user name supplied by the application, depending on the domain trust model that is used.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Example Code

The following example shows how to call this method to get the current user.

```
Dim Identification As SWbemObject
Dim UserName As String

Set Identification = GetObject("winmgmts:\root\sms\site_<sitecode>:SMS_Identification")
Identification.GetCurrentUser UserName

MsgBox "UserName = " & UserName
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).