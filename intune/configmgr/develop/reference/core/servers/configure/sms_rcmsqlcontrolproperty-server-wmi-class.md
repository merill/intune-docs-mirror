---
layout: Conceptual
title: SMS_RcmSqlControlProperty Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrolproperty-server-wmi-class
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
description: In Configuration Manager, the SMS_RcmSqlControlProperty Windows Management Instrumentation class is an SMS Provider server class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: be5205e8-bbd4-e21d-5703-b1edbfbdb014
document_version_independent_id: 1e0e5ccd-bf49-7dc8-bba8-7727c0c64dc3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrolproperty-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrolproperty-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_rcmsqlcontrolproperty-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a5958c33-77d0-9633-777f-41bff8e20f81
---

# SMS_RcmSqlControlProperty Class - Configuration Manager | Microsoft Learn

The `SMS_RcmSqlControlProperty` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_RcmSqlControlProperty :
{
    String PropertyName;
    UInt32 Value;
    String Value1;
    String Value2;
};
```

## Methods

The `SMS_RcmSqlControlProperty` class does not define any methods.

## Properties

`PropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the property.

`Value` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Property integer value.

`Value1` Data type: `String`

Access type: Read/Write

Qualifiers: none

First string value of the property.

`Value2` Data type: `String`

Access type: Read/Write

Qualifiers: none

Second string value of the property.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).