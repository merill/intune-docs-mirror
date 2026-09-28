---
layout: Conceptual
title: SMS_RcmSqlControl Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrol-server-wmi-class
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
description: The SMS_RcmSqlControl Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7f4a0de0-dd34-cc77-bc0c-65531de97132
document_version_independent_id: 1a377e52-2563-115e-547c-be6de9c1cb1d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrol-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrol-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrol-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 68cd0986-c6c6-f140-967a-2dc754ebf84b
---

# SMS_RcmSqlControl Class - Configuration Manager | Microsoft Learn

The `SMS_RcmSqlControl` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_RcmSqlControl :
{
    SMS_RcmSqlControlProperty Props[];
    String SiteCode;
    String TypeName;
};
```

## Methods

The `SMS_RcmSqlControl` class does not define any methods.

## Properties

`Props` Data type: `SMS_RcmSqlControlProperty` Array

Access type: Read/Write

Qualifiers: none

An array of `SMS_RcmSqlControlProperty` representing properties of the control.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

SiteCode.

`TypeName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

TypeName.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).