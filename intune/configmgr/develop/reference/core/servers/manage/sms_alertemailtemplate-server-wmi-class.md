---
layout: Conceptual
title: SMS_AlertEmailTemplate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alertemailtemplate-server-wmi-class
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
description: Learn how to represent the email template embedded by SMS_Subscription using SMS_AlertEmailTemplate.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2e418991-510f-1922-100d-c2ec7b461e06
document_version_independent_id: 68c486a1-bd63-75bc-cd70-baab96daa06b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_alertemailtemplate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_alertemailtemplate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_alertemailtemplate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7132d4e3-2647-58a3-7cab-0ab15e32c32d
---

# SMS_AlertEmailTemplate Class - Configuration Manager | Microsoft Learn

The `SMS_AlertEmailTemplate` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the email template embedded by `SMS_Subscription`.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AlertEmailTemplate
{
    UInt32 AlertID,
    String Subject
};
```

## Methods

The `SMS_AlertEmailTemplate` class does not define any methods.

## Properties

`AlertID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier of the alert.

`Subject` Data type: `String`

Access type: Read/Write

Qualifiers: none

Subject of the email.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).