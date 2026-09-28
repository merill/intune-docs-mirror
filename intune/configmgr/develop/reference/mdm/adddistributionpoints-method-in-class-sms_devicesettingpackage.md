---
layout: Conceptual
title: AddDistributionPoints method in class SMS_DeviceSettingPackage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/adddistributionpoints-method-in-class-sms_devicesettingpackage
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
description: Learn how to add the distribution points for the device setting package using the AddDistributionPoints class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a6f0566c-a312-e31c-c06e-794d5f5bf37e
document_version_independent_id: 908558e9-c1b1-6820-d3e3-0545b9c7af2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/adddistributionpoints-method-in-class-sms_devicesettingpackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/adddistributionpoints-method-in-class-sms_devicesettingpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/adddistributionpoints-method-in-class-sms_devicesettingpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4f966954-7d41-0bf4-de05-9cc056283c7a
---

# AddDistributionPoints method in class SMS_DeviceSettingPackage - Configuration Manager | Microsoft Learn

The `AddDistributionPoints` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds the distribution points for the device setting package.

Note

The `AddDistributionPoints` method allows a list of distribution points to be added to a package.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddDistributionPoints(
   String SiteCode[],
   String NALPath[]
);
```

#### Parameters

`SiteCode` Data type: `String` Array

Qualifiers: [in]

The code for the site to which to add the distribution points.

`NALPath` Data type: `String` Array

Qualifiers: [in]

Network abstraction layer (NAL) path to the distribution points.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

It is not necessary to refresh the distribution points when using this method.

## Requirements