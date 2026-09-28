---
layout: Conceptual
title: ActivateHierarchy method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/activatehierarchy-method-in-class-sms_migrationsitemapping
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
description: The technical details of the ActivateHierarchy method in the SMS_MigrationSiteMapping WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5477e135-d1ee-ec4f-833e-79e7d16db279
document_version_independent_id: f353b5f8-cf13-b764-5cad-c53498c1568a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/activatehierarchy-method-in-class-sms_migrationsitemapping.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/activatehierarchy-method-in-class-sms_migrationsitemapping
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/activatehierarchy-method-in-class-sms_migrationsitemapping.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 8f0bb32f-50cd-40da-59ce-77612105e709
---

# ActivateHierarchy method - Configuration Manager | Microsoft Learn

The `ActivateHierarchy` WMI class method in Configuration Manager activates the hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ActivateHierarchy (  
     String sourceSite,  
     String wmiAccount,  
     String sqlAccount,  
     String destinationSiteCode,  
     String scheduleToken  
);  
```

#### Parameters

`sourceSite` Data type: `String` Array

Qualifiers: [in]

The source site FQDN, netBIOS name or IP address.

`wmiAccount` Data type: `String` Array

Qualifiers: `[in]`

The account name to access the WMI provider on the source site.

`sqlAccount` Data type: `String` Array

Qualifiers: [in]

The account name to access SQL Server on the source site.

`destinationSiteCode` Data type: `String` Array

Qualifiers: `[in]`

The destination site's site code. This should be the top site.

`scheduleToken` Data type: `String` Array

Qualifiers: [in]

The schedule for the data gathering job.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).