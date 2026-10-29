---
layout: Conceptual
title: CreateCCRs method in class SMS_Query - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query
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
description: Learn how to generate client configuration requests (CCRs) for the query in Configuration Manager using CreateCCRs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c1907ba7-2716-9ea4-444b-6975da782994
document_version_independent_id: 29ac66bb-6bf4-7558-135c-103bc03d7e6f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 62461586-f9a9-e62b-fcef-7ad7bd5b91dc
---

# CreateCCRs method in class SMS_Query - Configuration Manager | Microsoft Learn

The `CreateCCRs` Windows Management Instrumentation (WMI) class method, in Configuration Manager, generates client configuration requests (CCRs) for the query.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 CreateCCRs(
   Boolean PushOnlyAssignedClients,
   SInt32 ClientType,
   Boolean Forced,
   Boolean ForceReinstall,
   Boolean PushEvenIfDC,
   Boolean InformationOnly,
   Boolean SpecifySiteCode,
   String PushSiteCode
);
```

#### Parameters

`PushOnlyAssignedClients` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to push installation only to assigned clients.

`ClientType` Data type: `SInt32`

Qualifiers: [in, optional]

Type of client.

`Forced` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to force installation. The value defaults to `false`, if not specified. This is used to force reinstallation, even if the client is already installed. If `Forced` is set to `true`, the operating system value will be ignored.

`ForceReinstall` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to force reinstallation. The value defaults to `false`, if not specified.

`PushEvenIfDC` Data type: `Boolean`

Qualifiers: [in, optional]

`true` to push installation on a domain component.

`InformationOnly` Data type: `Boolean`

Qualifiers: [in, optional]

`true` if the CCRs are for information only. This parameter is only used to gather information from the client.

`SpecifySiteCode` Data type: `Boolean`

Qualifiers: [in, optional]

`SpecifySiteCode` is used to control whether the `PushSiteCode` parameter is used. The `PushSiteCode` value will not be used unless `SpecificySiteCode` is set to `true`.

`PushSiteCode` Data type: `String`

Qualifiers: [in, optional]

`PushSiteCode` defines which site will initiate the actual push. The specified site will push its client files to the client and do the actual installation.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).