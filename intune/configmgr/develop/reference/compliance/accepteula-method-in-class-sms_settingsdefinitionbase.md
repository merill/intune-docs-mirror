---
layout: Conceptual
title: AcceptEULA Method in Class SMS_SettingsDefinitionBase - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/accepteula-method-in-class-sms_settingsdefinitionbase
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
description: The AcceptEULA Windows Management Instrumentation (WMI) class method accepts or declines the Microsoft Software License Terms of a configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 00c124f3-7b6e-0329-41d6-f9f2387ca861
document_version_independent_id: 7ab215c1-62ad-f334-8d35-9d7f15303ad4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/accepteula-method-in-class-sms_settingsdefinitionbase.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/accepteula-method-in-class-sms_settingsdefinitionbase
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/accepteula-method-in-class-sms_settingsdefinitionbase.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c073612-afb1-4839-905e-1e4e64e4567c
---

# AcceptEULA Method in Class SMS_SettingsDefinitionBase - Configuration Manager | Microsoft Learn

The `AcceptEULA` Windows Management Instrumentation (WMI) class method, in Configuration Manager, accepts or declines the Microsoft Software License Terms of a configuration item.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AcceptEULA(
      Boolean Accepted
);
```

#### Parameters

`Accepted` Data type: `Boolean`

Qualifiers: [in]

`true` to accept the license terms.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Your application should call this method only if the `EulaExists` property is set to `true` in the configuration item. This property is defined in the [SMS_ConfigurationItemBaseClass Server WMI Class](sms_configurationitembaseclass-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).