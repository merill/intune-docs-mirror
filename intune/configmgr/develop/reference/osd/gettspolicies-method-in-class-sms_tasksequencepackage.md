---
layout: Conceptual
title: GetTsPolicies Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/gettspolicies-method-in-class-sms_tasksequencepackage
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
description: The GetTsPolicies WMI class method gets all policies associated with the specified task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf8008a2-5007-bfd1-281c-d4b956fed4c7
document_version_independent_id: f3360e99-b93f-759a-2cba-65ac4f920f0e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/gettspolicies-method-in-class-sms_tasksequencepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/gettspolicies-method-in-class-sms_tasksequencepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/gettspolicies-method-in-class-sms_tasksequencepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a18e1684-69c2-ef5f-a5d5-1effbb709696
---

# GetTsPolicies Method - Configuration Manager | Microsoft Learn

The `GetTsPolicies` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets all policies associated with the specified task sequence. The user must have rights to create media other than stand-alone.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetTsPolicies(
     String AdvertisementID,
     String PackageID,
     SMS_TaskSequence TaskSequence,
     String AdvertisementName,
     String AdvertisementComment,
     UInt32 AdvertisementFlags,
     String BootImageID,
     String SourceSite,
     String PolicyXmls[],
     String PolicyAssignmentXmls[]
);
```

#### Parameters

`AdvertisementID` Data type: `String`

Qualifiers: [in]

A user-defined advertisement ID to embed in the policy. This ID should not conflict with other advertisement IDs that have been created by the site.

`PackageID` Data type: `String`

Qualifiers: [in]

The ID for the task sequence package, if the method is to obtain policy for a task sequence stored in the Configuration Manager database. Either `PackageID` or `TaskSequence` can be non-null, but not both parameters.

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: [in]

[SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) object representing the task sequence. Either `PackageID` or `TaskSequence` can be non-null, but not both parameters.

`AdvertisementName` Data type: `String`

Qualifiers: [in]

A user-defined name for the advertisement.

`AdvertisementComment` Data type: `String`

Qualifiers: [in]

A user-defined comment for the advertisement.

`AdvertisementFlags` Data type: `UInt32`

Qualifiers: [in]

User-defined flags specifying advertisement details. See [SMS_Advertisement Server WMI Class](../core/servers/configure/sms_advertisement-server-wmi-class) for more information about these flags.

`BootImageID` Data type: `String`

Qualifiers: [in]

The ID for a boot image package to use with the task sequence. This parameter is required if the `TaskSequence` parameter is defined. Otherwise, it must be set to `null`.

`SourceSite` Data type: `String`

Qualifiers: [in]

Code for the source site for the advertisement.

`PolicyXmls` Data type: `String` Array

Qualifiers: [out]

XML strings representing the policy for the specified task sequence and dependent policies.

`PolicyAssignmentXmls` Data type: `String` Array

Qualifiers: [out]

XML strings representing assignments for the policy specified by `PolicyXmls`. `PolicyXmls` and `PolicyAssignmentXmls` are aligned, with the nth element of one parameter corresponding to the nth element of the other.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

The policies for a task sequence include the policy for the task sequence itself, policies for all referenced packages, and corresponding policy assignments. The task sequence can be stored either in the database or in memory as a set of WMI objects.

If the task sequence is in the Configuration Manager database, your application should specify the package identifier for the task sequence package in the `PackageID` parameter. If supplying a value for this parameter, you must have read permission for the specific task sequence.

If the task sequence is in memory, your application must specify values for the `TaskSequence` and `BootImageID` parameters.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).