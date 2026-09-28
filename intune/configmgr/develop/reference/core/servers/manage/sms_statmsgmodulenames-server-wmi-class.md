---
layout: Conceptual
title: SMS_StatMsgModuleNames Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class
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
description: Learn how to map module names to the message DLL containing the status message text using SMS_StatMsgModuleNames.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5fcfa7d1-2753-abac-1fd7-7d4234575e48
document_version_independent_id: ca248668-6ad1-bc2f-c920-e62ae9b69046
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b0b43dae-2bc3-3b6d-5a31-ad1772dd90d6
---

# SMS_StatMsgModuleNames Class - Configuration Manager | Microsoft Learn

The `SMS_StatMsgModuleNames` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps module names to the message DLL that contains the status message text.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StatMsgModuleNames : SMS_BaseClass
{
    String ModuleName;
    String MsgDLLName;
};
```

## Methods

The `SMS_StatMsgModuleNames` class does not define any methods.

## Properties

`ModuleName` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

Module name as used in the `ModuleName` property of [SMS_StatusMessage Server WMI Class](sms_statusmessage-server-wmi-class).

`MsgDLLName` Data type: `String`

Access type: Read

Qualifiers: None

Name of the corresponding resource DLL that contains the text of the message.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).