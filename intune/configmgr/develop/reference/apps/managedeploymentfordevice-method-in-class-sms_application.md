---
layout: Conceptual
title: ManageDeploymentForDevice Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/managedeploymentfordevice-method-in-class-sms_application
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
description: The following syntax is simplified from Managed Object Format (MOF) code and defines the method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7e42996e-21ec-6aa1-b466-185fa8b9598f
document_version_independent_id: 79f4ab19-a1f4-3c46-6c12-a26f000fa5dc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/managedeploymentfordevice-method-in-class-sms_application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/managedeploymentfordevice-method-in-class-sms_application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/managedeploymentfordevice-method-in-class-sms_application.md
cmProducts: []
platformId: bb0f7f55-3e08-8741-fdf3-e733696059c6
---

# ManageDeploymentForDevice Method - Configuration Manager | Microsoft Learn

Warning

This method is reserved for future use.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ManageDeploymentForDevice (
     String   AssignmentUniqueID,
     String   ClientGUID,
     UInt32   Action
);

```

#### Parameters

`AssignmentUniqueID` Data type: `String`

Qualifiers: [in]

Identifier for the application deployment.

`ClientGUID` Data type: `String`

Qualifiers: [in]

Unique identifier of a client.

`Action` Data type: `UInt32`

Qualifiers: [in, enumeration]

Activate or deactivate deployment. Possible values are:

| Value | Activate or deactivate |
| --- | --- |
| 1 | Activate |
| 2 | Deactivate |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).