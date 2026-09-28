---
layout: Conceptual
title: SMS_ConfigurationItemRules Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class
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
description: Learn how to represent configuration item rules using SMS_ConfigurationItemRules in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c0ffe869-da07-09df-96f3-9af5e08c87e7
document_version_independent_id: 9eb8f169-0c00-1c96-390a-7fc811137812
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1a6e98c2-a389-6089-58ee-519cb53200d0
---

# SMS_ConfigurationItemRules Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigurationItemRules` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents configuration item rules.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItemRules : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    String ModelName;
    UInt32 Rule_ID;
    String Rule_UniqueID;
    String RuleDescription;
    String RuleName;
};
```

## Methods

The `SMS_ConfigurationItemRules` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`Rule_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The database identifier of a rule defined in a configuration item.

`Rule_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Uniquely identifies a rule defined in the configuration item and is used for reporting rule level details.

`RuleDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the rule.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_CollectionRule Server WMI Class](../core/clients/collections/sms_collectionrule-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).