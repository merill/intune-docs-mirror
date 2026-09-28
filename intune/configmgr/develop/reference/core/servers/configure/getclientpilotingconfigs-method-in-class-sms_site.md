---
layout: Conceptual
title: GetClientPilotingConfigs Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getclientpilotingconfigs-method-in-class-sms_site
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
description: In Configuration Manager, the GetClientPilotingConfigs WMI class method gets the configurations for client piloting settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d5acc1cb-9843-da48-f516-776cc59849c5
document_version_independent_id: 3a5c65d3-c9d1-9b7d-940a-274bbc53678b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getclientpilotingconfigs-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getclientpilotingconfigs-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getclientpilotingconfigs-method-in-class-sms_site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a2cba6a8-39b8-4321-7f58-0ff13f832950
---

# GetClientPilotingConfigs Method - Configuration Manager | Microsoft Learn

The `GetClientPilotingConfigs` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the configurations for client piloting settings.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetClientPilotingConfigs (
    Boolean IsEnabled,
    Boolean IsAccepted,
    String TargetCollectionID,
    Datetime LastModifiedTime,
    String LastModifiedBy
);

```

#### Parameters

`IsEnabled` Data type: `Boolean`

Qualifiers: [out]

Indicates whether client piloting testing mode is enabled.

`IsAccepted` Data type: `Boolean`

Qualifiers: [out]

Indicates whether the new client binaries are accepted. If `IsEnabled` is `true`, this parameter is ignored and is always `false`.

`TargetCollectionID` Data type: `String`

Qualifiers: [out]

Targeted collection ID.

`LastModifiedTime` Data type: `Datetime`

Qualifiers: [out]

The time that the last modification was made.

`LastModifiedBy` Data type: `String`

Qualifiers: [out]

The user name of the user who made the last modification.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).