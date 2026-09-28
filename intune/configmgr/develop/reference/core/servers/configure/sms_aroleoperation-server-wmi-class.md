---
layout: Conceptual
title: SMS_ARoleOperation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_aroleoperation-server-wmi-class
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
description: An SMS Provider server class that SMS_Role embeds, and this class describes the operation granted to this role.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 76826c5f-a4b1-dada-39a8-596d2cff8c76
document_version_independent_id: 542a615b-b486-d51f-d6ba-58c62e605e08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_aroleoperation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_aroleoperation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_aroleoperation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 00b7fb04-12ca-d64f-081b-a15f27966cee
---

# SMS_ARoleOperation Class - Configuration Manager | Microsoft Learn

The `SMS_ARoleOperation` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that the SMS\_Role embeds, and this class describes the operation that is granted to this role.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ARoleOperation : SMS_BaseClass
{
    UInt32 GrantedOperations;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_ARoleOperation` class doesn't define any methods.

## Properties

`GrantedOperations` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

A bit mask representing the granted operations. Possible values are:

| N | 2^N | Granted operation |
| --- | --- | --- |
| 0 | 1 | Read |
| 1 | 2 | Modify |
| 2 | 4 | Delete |
| 3 | 8 | Copy to Distribution Point |
| 4 | 16 | Set Security Scope |
| 5 | 32 | Remote Control |
| 6 | 64 | Not Used |
| 7 | 128 | Modify Resource |
| 8 | 256 | Not Used |
| 9 | 512 | Delete Resource |
| 10 | 1024 | Create Admin.Add |
| 11 | 2048 | View Collected File Application.Approve |
| 12 | 4096 | Read Resource |
| 13 | 8192 | Manage Folder Item |
| 14 | 16384 | Meter Site Collection.Deploy Packages |
| 15 | 32768 | Not Used |
| 16 | 65536 | Manage Status Filters Collection.Deploy Client Settings |
| 17 | 131072 | Manage Folder |
| 18 | 262144 | ConfigurationItem.Network Access Site.Modify CH Settings Collection.EnforceSecurity SMS\_AntimalwareSettings.ReadDefault |
| 19 | 524288 | Site.Import Machine Collection.Deploy Antimalware Settings |
| 20 | 1048576 | SequencePackage.Create Task Sequence Media SMS\_DistributionPointGroup.Associate SMS\_BoundaryGroup.AssociateSiteSystem SMS\_SettingsDefinition.ModifyPolicy Collection.Deploy Applications |
| 21 | 2097152 | Collection.Modify Collection Settings Site.ModifyConnectorPolicy SMS\_AntimalwareSettings.ModifyDefault |
| 22 | 4194304 | Site.Manage OSD Certificate MigrationJob.Manage MigrationSiteMapping.SpecifySourceHierarchy Collection.Deploy Configuration Items |
| 23 | 8388608 | StateMigration.Recover User State Collection.Deploy Task Sequences |
| 24 | 16777216 | Collection.Manage BMC |
| 25 | 33554432 | Collection.View BMC |
| 26 | 67108864 | AISoftwareList.Manage AI Collection.Deploy Software Updates |
| 27 | 134217728 | AISoftwareList.View AI Collection.Deploy Firewall Policies |
| 28 | 268435456 | RunReport |
| 29 | 536870912 | ModifyReport |

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the object type ID. See `SMS_RbacSecuredObject` for a list of secured object types.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).