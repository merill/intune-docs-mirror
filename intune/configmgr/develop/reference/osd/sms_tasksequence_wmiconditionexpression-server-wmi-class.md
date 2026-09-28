---
layout: Conceptual
title: SMS_TaskSequence_WMIConditionExpression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class
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
description: Represents a condition expression to check for the existence of results of a WMI query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 31f0f35e-4b9d-daae-99c3-7f5e89a0116a
document_version_independent_id: 7ef2d54f-fea2-33e1-0379-97921cc79227
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 42f93a1e-ce64-ee2f-09f8-c4f7a782df86
---

# SMS_TaskSequence_WMIConditionExpression Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_WMIConditionExpression` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a condition expression to check for the existence of results of a WMI query.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_WMIConditionExpression : SMS_TaskSequence_ConditionExpression
{
      String Namespace;
      String Query;
};
```

## Methods

The `SMS_TaskSequence_WMIConditionExpression` class does not define any methods.

## Properties

`Namespace` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Namespace for the query.

`Query` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, AllowedLen("1-16384")]

The WQL query for the condition expression. The length is between 1 and 16,384 characters.

## Remarks

The query result set is the results that satisfy the condition. For example, if you need to identify if a computer has at least one NTFS partition, you would use the following query:

```
Select * from win32_logicaldisk where FileSystem='NTFS'
```

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).