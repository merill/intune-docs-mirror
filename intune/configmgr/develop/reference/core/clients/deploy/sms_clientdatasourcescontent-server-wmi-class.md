---
layout: Conceptual
title: SMS_ClientDataSourcesContent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcescontent-server-wmi-class
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
description: The SMS_ClientDataSourcesContent Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8fd66617-b0fc-c3ae-96f4-ff607bd53a36
document_version_independent_id: 5cb5aa06-3701-3b69-5911-8af88c5d10e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcescontent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcescontent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcescontent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eb07f07a-1dcc-332e-8c52-0933c4eed51b
---

# SMS_ClientDataSourcesContent Class - Configuration Manager | Microsoft Learn

The `SMS_ClientDataSourcesContent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents client content data sources per boundary group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDataSourcesContent : SMS_BaseClass
{
    UInt64 BranchCacheBytes;
    UInt64 CloudDistributionPointBytes;
    UInt64 DistributionPointBytes;
    UInt32 DpSourceServerCount;
    UInt64 PeerCacheBytes;
    UInt32 SpSourceClientCount;
};

```

## Methods

The `SMS_ClientDataSourcesContent` class does not define any methods.

## Properties

`BranchCacheBytes` Data type: `UInt64`

Access type: Read

Qualifiers: none

Number of bytes from the branch cache.

`CloudDistributionPointBytes` Data type: `UInt64`

Access type: Read

Qualifiers: none

Number of bytes from cloud distribution points.

`DistributionPointBytes` Data type: `UInt64`

Access type: Read

Qualifiers: none

Number of bytes from distribution points.

`DpSourceServerCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

Number of distribution points that served content.

`PeerCacheBytes` Data type: `UInt64`

Access type: Read

Qualifiers: none

Number of bytes from the peer cache.

`SpSourceClientCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

Number of super peers that served content.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)
- Singleton
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).