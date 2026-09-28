---
layout: Conceptual
title: SMS_TaskSequence_FolderConditionExpression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_folderconditionexpression-server-wmi-class
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
description: An SMS Provider server class that represents a condition expression to check for the existence of a folder and when it was created.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d5d97015-d3f5-1b5c-32e1-86bee7553f1a
document_version_independent_id: e1be0fa9-f317-28a0-806c-983f7a165560
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_folderconditionexpression-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_folderconditionexpression-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_folderconditionexpression-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 48db73c4-8999-7545-a3ce-f8cca1719b62
---

# SMS_TaskSequence_FolderConditionExpression Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_FolderConditionExpression` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a condition expression to check for the existence of a folder and when it was created.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_FolderConditionExpression : SMS_TaskSequence_ConditionExpression
{
      DateTime DateTime;
      String DateTimeOperator;
      String Path;
};
```

## Methods

The `SMS_TaskSequence_FolderConditionExpression` class does not define any methods.

## Properties

`DateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time used to evaluate the target computer for a specific, user-specified timestamp on a folder.

The timestamp that is displayed in the Configuration Manager console is the local time on the computer running the Configuration Manager console. The timestamp is converted to Coordinated Universal Time (UTC). The comparison on the target computer uses the UTC timestamp so that time zones and daylight savings time do not affect the comparison.

`DateTimeOperator` Data type: `String`

Access type: Read/Write

Qualifiers: None

The date and time operator. Possible values are:

- equals
- notEquals
- less
- lessEqual
- greater
- greaterEqual

    `Path` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null]

    The path on the target computer for the folder that is being verified. The path can contain embedded task sequence and system environment variables, for example, %*windir*%\Temp.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Note

The evaluation of the path is affected by the value of the SMSTSDisableWow64Redirection environment variable.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).