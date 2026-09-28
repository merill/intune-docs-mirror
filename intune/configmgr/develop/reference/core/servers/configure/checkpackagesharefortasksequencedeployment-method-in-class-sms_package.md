---
layout: Conceptual
title: CheckPackageShareForTaskSequenceDeployment Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/checkpackagesharefortasksequencedeployment-method-in-class-sms_package
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
description: Learn how to use the Configuration Manager with the CheckPackageShareForTaskSequenceDeployment Windows Management Instrumentation (WMI) class method to verify that the package share type meets the requirements of a task sequence deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 94e0dd58-555f-8a10-23d4-e3bf9a51d4f0
document_version_independent_id: cf40203e-e6c2-7dab-77fa-7e430a90bb34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/checkpackagesharefortasksequencedeployment-method-in-class-sms_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/checkpackagesharefortasksequencedeployment-method-in-class-sms_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/checkpackagesharefortasksequencedeployment-method-in-class-sms_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eb893cd6-ad2b-4236-16cc-e2595e58dca5
---

# CheckPackageShareForTaskSequenceDeployment Method - Configuration Manager | Microsoft Learn

The `CheckPackageShareForTaskSequenceDeployment` Windows Management Instrumentation (WMI) class method in Configuration Manager that checks whether the package share type meets the requirements of a task sequence deployment.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 CheckPackageShareForTaskSequenceDeployment
{
    [IN]    String PackageID
    [OUT]   Boolean IsValid
    [OUT]   String InvalidTaskSequenceDeploymentIDs[]
    [OUT]   String InvalidTaskSequenceDeploymentNames[]
};
```

## Parameters

`PackageID` Data type: `String`

Qualifiers: [id("0"), in]

Package identifier.

`IsValid` Data type: `Boolean`

Qualifiers: [id("1"), out]

`true` if the package is valid for task sequence use. `false` if the package is invalid for task sequence use. If the package is referred to by a run-from-net deployment, the package must be available as a share on a distribution point.

`InvalidTaskSequenceDeploymentIDs` Data type: `String` Array

Qualifiers: [id("2"), out]

Identifiers of task sequence deployments that are invalid because this package isn't valid for task sequence use.

`InvalidTaskSequenceDeploymentNames` Data type: `String Array`

Qualifiers: [id("3"), out]

Names of task sequence deployments that are invalid because this package isn't valid for task sequence use.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).