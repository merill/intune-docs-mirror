---
layout: Conceptual
title: GenerateProvisioningXML Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles
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
description: The ImportForProfile Windows Management Instrumentation (WMI) class method generates provisioning data in XML format.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9061c376-bb83-fc0e-2252-0e0a0a2f0b13
document_version_independent_id: 2b233cfb-d0ec-817a-4455-4258579c3e25
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79fc87d1-9355-62cc-36df-9699f983aa5c
---

# GenerateProvisioningXML Method - Configuration Manager | Microsoft Learn

The `ImportForProfile` Windows Management Instrumentation (WMI) class method, in Configuration Manager, generates provisioning data in XML format.

## Syntax

```
sint32 GenerateProvisioningXML(
     String BulkEnrollmentProfileID,
     Boolean IsEncrypted,
     String EncrytionPassword,
     String ProvisioningDataXML
);

```

#### Parameters

`BulkEnrollmentProfileID` Data type: `String`

Qualifiers: [in]

The ID of the bulk enrollment profile.

`IsEncrypted` Data type: `Boolean`

Qualifiers: [in]

`true` if the enrollment package is password-protected. The default value is `false`.

`EncrytionPassword` Data type: `String`

Qualifiers: [in, optional]

The password used to encrypt the enrollment package.

`ProvisioningDataXML` Data type: `String`

Qualifiers: [out]

The XML output that contains the provisioning data.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).