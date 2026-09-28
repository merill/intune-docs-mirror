---
layout: Conceptual
title: GetDeployments Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/getdeployments-method-in-class-sms_deployment_info
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
description: The GetDeployments Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets advertisement identifier or Assignment identifier and related type for a deployment that is deployed to the specified resource.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 980545e2-48ba-dbec-23a1-4c589ff40f3b
document_version_independent_id: 6b862ed7-e826-9f8c-9889-7d38edebf6b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/getdeployments-method-in-class-sms_deployment_info.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/getdeployments-method-in-class-sms_deployment_info
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/getdeployments-method-in-class-sms_deployment_info.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4fac138f-0db0-71df-0cc8-7fbeca4c1ea2
---

# GetDeployments Method - Configuration Manager | Microsoft Learn

The `GetDeployments` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets advertisement identifier or Assignment identifier and related type for a deployment that is deployed to the specified resource.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 GetDeployments(
     uint32 ResourceID,
     string DeploymentIDs[],
     uint32 DeploymentTypeID[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: [in]

Configuration Manager supplied ID for the resource. This ID is not unique across sites.

`DeploymentIDs` Data type: `String` Array

Qualifiers: [out]

Unique auto-generated key for the deployment.

`DeploymentTypeID` Data type: `UInt32` Array

Qualifiers: [out]

Type identifier of the deployment.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).