---
layout: Conceptual
title: InventoryDataContext Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventorydatacontext-client-wmi-class
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
description: In Configuration Manager, the InventoryDataContext class is a client WMI class that represents the WMI context qualifiers to be used with inventory client agent WMI queries built from InventoryDataItem Client WMI class objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8449a19c-00cd-bf66-348d-c8aa86f699d5
document_version_independent_id: 349587d3-77e9-9e3b-3731-14e783b30d85
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/inventorydatacontext-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/inventorydatacontext-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/inventorydatacontext-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 8cc95289-39e4-c607-709b-6366bfc8c922
---

# InventoryDataContext Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `InventoryDataContext` class is a client Windows Management Instrumentation (WMI) class that represents the WMI context qualifiers to be used with inventory client agent WMI queries built from [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) objects. Typically, dynamic instance providers do not require context qualifiers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class InventoryDataContext : SMS_InventoryAgent_EmbeddedObject
{
    String Name;
    String Type;
    String Value[];
};
```

## Methods

The `InventoryDataContext` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

Name of the context qualifier.

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: None

String representation of the WMI variant data type for the context qualifier (for example, 3 for integer and 8200 for string array).

`Value` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Context qualifier value, consistent with the specified data type.

## Remarks

This class allows a generic method to specify context qualifiers for a WMI class query when they are needed. For example, the File System Inventory provider allows context qualifiers for specifying an amount of time to delay between back-to-back file operations. If no context qualifier is specified, there is no delay or throttling of scanning files on the system disk.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).