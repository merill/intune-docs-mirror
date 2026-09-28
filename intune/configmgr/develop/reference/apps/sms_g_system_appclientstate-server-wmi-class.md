---
layout: Conceptual
title: SMS_G_System_AppClientState Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_appclientstate-server-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: The `SMS_G_System_AppClientState` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents application state.
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 14f15414-267b-e658-4946-fde7b44eb754
document_version_independent_id: 9541c6c7-5fd4-e78d-d5fa-a2f95d12fb42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_g_system_appclientstate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_g_system_appclientstate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_g_system_appclientstate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 559360f4-d8cd-8dea-6d54-32a2f50ae727
---

# SMS_G_System_AppClientState Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_AppClientState` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents application state.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_AppClientState : SMS_G_System
{
    UInt32 AppCI;
    UInt32 AppModelID;
    String AppModelName;
    String AppName;
    UInt32 ComplianceState;
    String MachineName;
    UInt32 ResourceID;
    UInt32 Revision;
    String UserName;
};
```

## Methods

The `SMS_G_System_AppClientState` class does not define any methods.

## Properties

`AppCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AppModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the application model.

`AppModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the Application Model.

`AppName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Resource ID.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).