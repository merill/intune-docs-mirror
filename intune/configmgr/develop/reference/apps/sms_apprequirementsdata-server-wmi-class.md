---
layout: Conceptual
title: SMS_AppRequirementsData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_apprequirementsdata-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents the requirements data of an application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ef7f846c-0419-501d-22de-0c72941b53fc
document_version_independent_id: 56131c7e-6ab2-8c8e-483d-837697564b43
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_apprequirementsdata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_apprequirementsdata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_apprequirementsdata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f3c4d9f3-77af-47fb-832b-1be1051e64cc
---

# SMS_AppRequirementsData Class - Configuration Manager | Microsoft Learn

The `SMS_AppRequirementsData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the requirements data of an application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AppRequirementsData : SMS_BaseClass
{
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    String CollectionID;
    UInt32 DTCI;
    UInt64 DTResultID;
    UInt32 InstanceGroup;
    String MachineName;
    String RequirementName;
    UInt32 RuleID;
    String SettingName;
    String SettingValue;
    String UniqueRequirementName;
    String UserName;
};
```

## Methods

The `SMS_AppRequirementsData` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTCI` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`DTResultID` Data type: `UInt64`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`InstanceGroup` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Instance group.

`MachineName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_AppDeploymentAssetDetails Server WMI Class](sms_appdeploymentassetdetails-server-wmi-class).

`RequirementName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of the requirement.

`RuleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Identifier of the rule.

`SettingName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Name of the setting.

`SettingValue` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Setting value.

`UniqueRequirementName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Unique requirement name.

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