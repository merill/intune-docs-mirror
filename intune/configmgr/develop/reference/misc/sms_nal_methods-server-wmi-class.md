---
layout: Conceptual
title: SMS_NAL_Methods Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class
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
description: The `SMS_NAL_Methods` Windows Management Instrumentation (WMI) class, in Configuration Manager, defines and manipulates a network abstraction layer (NAL) path.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 07df4691-2ae3-d45f-396f-a21deb514b53
document_version_independent_id: c959a493-0e60-39e5-042a-034a8e88b233
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cccf7443-10d4-2c40-0924-9fc73d41cbd7
---

# SMS_NAL_Methods Class - Configuration Manager | Microsoft Learn

The `SMS_NAL_Methods` Windows Management Instrumentation (WMI) class, in Configuration Manager, defines and manipulates a network abstraction layer (NAL) path.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_NAL_Methods : SMS_BaseClass ();

```

## Methods

The following table lists the methods in `SMS_NAL_Methods`.

| Method | Description |
| --- | --- |
| [PackNALPath](packnalpath-method-in-class-sms_nal_methods) | Encodes a NAL path from its components. |
| [UnPackNALPath](unpacknalpath-method-in-class-sms_nal_methods) | Decodes a NAL path into its components. |

## Properties

The `SMS_NAL_Methods` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).