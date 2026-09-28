---
layout: Conceptual
title: SetDPMaintenanceMode method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setdpmaintenancemode-method-in-class-sms-distributionpointinfo
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
description: Learn how to set a distribution point in maintenance mode using SetDPMaintenanceMode class method in Configuration Manager.
ms.date: 2019-05-24T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 52f29894-1716-97fe-3a66-aa234e5ed30e
document_version_independent_id: c574962d-270b-82a2-7b30-531ae10246d4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/setdpmaintenancemode-method-in-class-sms-distributionpointinfo.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/setdpmaintenancemode-method-in-class-sms-distributionpointinfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/setdpmaintenancemode-method-in-class-sms-distributionpointinfo.md
cmProducts: []
platformId: a16a3423-b3af-2efc-293b-1940c88c9bb0
---

# SetDPMaintenanceMode method - Configuration Manager | Microsoft Learn

The `SetDPMaintenanceMode` WMI class method in Configuration Manager sets a distribution point in maintenance mode. For more information, see [Maintenance mode](../../../../../core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_maint).

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```MOF
uint32 SetDPMaintenanceMode(
    [in] string NALPath,
    [in] uint32 Mode
);
```

## Parameters

### `NALPath`

Data type: `String`

Qualifiers: `[in]`

Network abstraction layer (NAL) path to the distribution point server.

### `Mode`

Data type: `uint32`

Qualifiers: `[in]`

`1` to enable maintenance mode, `0` to disable

## Return values

An `uint32` data type that's `0` indicates success. A non-zero hresult indicates failure.

For more information about handling returned errors, see [About Configuration Manager errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).