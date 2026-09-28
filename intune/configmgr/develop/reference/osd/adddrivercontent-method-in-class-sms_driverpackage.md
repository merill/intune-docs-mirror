---
layout: Conceptual
title: AddDriverContent Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage
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
description: In Configuration Manager, the AddDriverContent Windows Management Instrumentation class method adds a driver to the driver package and replicates the driver content to distribution points.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 475610e4-23eb-4071-0c8d-ba2c7088e11a
document_version_independent_id: bcae498b-feb9-4d4f-073a-9b60dbfdfc01
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 55b1acc3-72b2-e226-64b4-26f8d7a06a20
---

# AddDriverContent Method - Configuration Manager | Microsoft Learn

The `AddDriverContent` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds a driver to the driver package and replicates the driver content to distribution points.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddDriverContent(
     UInt32 ContentIDs[],
     String ContentSourcePath[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: [in]

The IDs for content to add to the driver package.

`ContentSourcePath` Data type: `String` Array

Qualifiers: [in]

The source paths where the content files are located. In most cases, these paths should be the same as the settings for the `ContentSourcePath` properties of the [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) objects represented by the driver package. The paths can be overridden with local paths if the SMS Provider does not have access to the central site for Configuration Manager.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: [in, optional]

`true`, by default, if driver package content is to be replicated to the distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

An example of the use of this method is provided in [How to Create a Driver Package for a Windows Driver in Configuration Manager](../../osd/how-to-create-a-driver-package-for-a-windows-driver).

If the call to this method fails, check the Smsprov.log file on the provider computer for more information.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).