---
layout: Conceptual
title: SMS_ContextMethods Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class
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
description: The SMS_ContextMethods Windows Management Instrumentation (WMI) class is an abstract class in Configuration Manager that contains methods for caching WMI context qualifiers with the SMS Provider.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ddf943d4-6a43-17db-b867-369fce4e5c96
document_version_independent_id: 2c293df4-de9a-1e53-de6a-58582e265bda
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0bfd2754-e1e1-19af-a250-265940bd3d10
---

# SMS_ContextMethods Class - Configuration Manager | Microsoft Learn

The `SMS_ContextMethods` Windows Management Instrumentation (WMI) class is an abstract class in Configuration Manager that contains methods for caching WMI context qualifiers with the SMS Provider.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ContextMethods ();
```

## Methods

The following table lists the methods in `SMS_ContextMethods`.

| Term | Description |
| --- | --- |
| [ClearContextHandle Method in Class SMS_ContextMethods](clearcontexthandle-method-in-class-sms_contextmethods) | Releases cached context data. |
| [GetContextHandle Method in Class SMS_ContextMethods](getcontexthandle-method-in-class-sms_contextmethods) | Caches multiple context qualifiers within the SMS Provider. This allows applications to use a much smaller context object when making API calls to WMI. |

## Properties

The `SMS_ContextMethods` class doesn't define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).