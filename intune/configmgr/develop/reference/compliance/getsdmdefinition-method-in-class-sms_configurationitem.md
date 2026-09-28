---
layout: Conceptual
title: GetSDMDefinition Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem
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
description: Learn how to retrieve the System Definition Model (SDM) definition of the configuration item in XML format using GetSDMDefinition class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bc922e61-ad37-1ffb-952b-284e13751dd4
document_version_independent_id: 536e6904-6bbe-a4bb-7c5c-95865ebbaab9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6af435b9-6de5-324c-9354-ead6cd44fe1c
---

# GetSDMDefinition Method - Configuration Manager | Microsoft Learn

The `GetSDMDefinition` Windows Management Instrumentation (WMI) class method, in Configuration Manager, retrieves the System Definition Model (SDM) definition of the configuration item in XML format.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetSDMDefinition(
     String SDMDefinition
);
```

#### Parameters

`SDMDefinition` Data type: `String`

Qualifiers: [out]

The SDM definition in XML format.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

For more information about SDM definitions, see About Authoring Configuration Baselines and Configuration Items.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).