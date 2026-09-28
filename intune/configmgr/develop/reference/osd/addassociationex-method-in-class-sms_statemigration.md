---
layout: Conceptual
title: AddAssociationEx Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociationex-method-in-class-sms_statemigration
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
description: Adds the computer association between two system resources used in state migration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dbc27f7b-8b2b-2eb1-d2d0-eec7518fb666
document_version_independent_id: 65d9243c-754c-b5e3-3977-2b3b578eb5ae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/addassociationex-method-in-class-sms_statemigration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/addassociationex-method-in-class-sms_statemigration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/addassociationex-method-in-class-sms_statemigration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8caa0fcc-96e7-e885-4e25-25d0d9e3b566
---

# AddAssociationEx Method - Configuration Manager | Microsoft Learn

The `AddAssociationEx` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds the computer association between two system resources used in state migration.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddAssociationEx(
      UInt32 SourceClientResourceID,
      UInt32 RestoreClientResourceID,
      UInt32 MigrationBehavior,
      SMS_StateMigrationUserNames UserNames[]
);
```

#### Parameters

`SourceClientResourceID` Data type: `UInt32`

Qualifiers: [in]

Resource ID for the source client.

`RestoreClientResourceID` Data type: `UInt32`

Qualifiers: [in]

Resource ID for the destination client.

`MigrationBehavior` Data type: `UInt32`

Qualifiers: [in]

Migration behavior. Possible values are:

| Value | Migration behavior |
| --- | --- |
| 0 | CAPTUREANDRESTOREALL |
| 1 | CAPTUREALLRESTORESPECIFIED |
| 2 | CAPTUREANDRESTORESPECIFIED |

`UserNames` Data type: `SMS_StateMigrationUserNames` Array

Qualifiers: [in]

[SMS_StateMigrationUserNames Server WMI Class](sms_statemigrationusernames-server-wmi-class) objects representing the names of users with profiles to be migrated. These objects are defined by the `UserNames` property of [SMS_StateMigration Server WMI Class](sms_statemigration-server-wmi-class).

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

For an example of the use of this method, see [How to Create an Association Between Two Computers in Configuration Manager](../../osd/how-to-create-an-association-between-two-computers-in-configuration-manager). To remove an association, your application can call the [DeleteAssociation Method in Class SMS_StateMigration](deleteassociation-method-in-class-sms_statemigration).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).