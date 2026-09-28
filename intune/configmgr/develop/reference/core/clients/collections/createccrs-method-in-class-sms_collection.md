---
layout: Conceptual
title: CreateCCRs method in class SMS_Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/createccrs-method-in-class-sms_collection
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
description: Article describing the use of CreateCCRs in Configuration Manager to generate client configuration requests for the computers in the collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5c3b888c-4416-5690-6bb1-35b0516f9d5c
document_version_independent_id: b5eea103-4a0a-35ab-7b9e-753480762150
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/createccrs-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/createccrs-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/createccrs-method-in-class-sms_collection.md
cmProducts: []
platformId: 14b4f0df-b389-9006-919d-910974a7f30c
---

# CreateCCRs method in class SMS_Collection - Configuration Manager | Microsoft Learn

The `CreateCCRs` WMI class method, in Configuration Manager, generates client configuration requests (CCRs) for the computers in the collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CreateCCRs(
     Boolean IncludeSubCollections,
     Boolean PushOnlyAssignedClients,
     SInt32 ClientType,
     Boolean Forced,
     Boolean ForceReinstall,
     Boolean PushEvenIfDC,
     Boolean InformationOnly
     Boolean SpecifySiteCode,
     String PushSiteCode)
);
```

#### Parameters

`IncludeSubCollections` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to include subcollections. This value defaults to false, if not specified.

`PushOnlyAssignedClients` Data type: `Boolean`

Qualifiers: [in, optional]

This property is deprecated.

`ClientType` This property is deprecated.

`Forced` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to force installation. This defaults to false, if not specified. This is used for force reinstallation, even if the client is already installed. If set to `true`, the operating system is ignored.

`ForceReinstall` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to force reinstallation. This defaults to false, if not specified.

`PushEvenIfDC` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to push installation on a domain component. This defaults to false, if not specified.

`InformationOnly` Data type: `Boolean`

Qualifiers: [in, optional]

`true` if the CCRs are for information only. This parameter is only used to gather information from the client. This defaults to false, if not specified.

`SpecifySiteCode` Data type: `Boolean`

Qualifiers: [in, optional]

`SpecifySiteCode` is used to control whether the `PushSiteCode` parameter is used. If `SpecificySiteCode` is set to `true`, `PushSiteCode` is used. If `SpecificySiteCode` isn't set to `true`, `PushSiteCode` won't be used.

`PushSiteCode` Data type: `Boolean`

Qualifiers: [in, optional]

`PushSiteCode` defines which site initiates the actual push. The specified site pushes its client files to the client and do the actual installation.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).