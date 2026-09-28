---
layout: Conceptual
title: RiskyDeploymentStatusMessage Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/riskydeploymentstatusmessage-method-in-class-sms_advertisement
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
description: Learn how to use the RiskyDeploymentStatusMessage method to send a warning status message about a user deployment to a risky collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e28761d8-19e6-e8de-ea89-59e9dcdb6a0d
document_version_independent_id: a28c779d-2eb9-302c-269c-88c4b86e5586
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/riskydeploymentstatusmessage-method-in-class-sms_advertisement.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/riskydeploymentstatusmessage-method-in-class-sms_advertisement
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/riskydeploymentstatusmessage-method-in-class-sms_advertisement.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9401da35-95b7-871d-b23e-c746d6c16b20
---

# RiskyDeploymentStatusMessage Method - Configuration Manager | Microsoft Learn

The `RiskyDeploymentStatusMessage` Windows Management Instrumentation (WMI) class method, in Configuration Manager, sends a warning status message about a user deployment to a risky collection.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 RiskyDeploymentStatusMessage (
    String DeploymentID,
    String DeploymentName,
    String PackageID,
    String CollectionID
);

```

#### Parameters

`DeploymentID` Data type: `String`

Qualifiers: [in]

Deployment ID.

`DeploymentName` Data type: `String`

Qualifiers: [in]

Name of the deployment.

`PackageID` Data type: `String`

Qualifiers: [in]

Package ID of the deployment.

`CollectionID` Data type: `String`

Qualifiers: [in]

Collection ID of the deployment.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).