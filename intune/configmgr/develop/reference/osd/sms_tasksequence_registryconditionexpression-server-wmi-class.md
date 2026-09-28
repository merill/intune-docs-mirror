---
layout: Conceptual
title: SMS_TaskSequence_RegistryConditionExpression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class
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
description: Learn how to represent a condition expression to check for the existence of a registry key and compare it to data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d029af37-beb1-924c-fcb4-1ba4897b135a
document_version_independent_id: a70b0ec2-90e5-c6c9-54ce-0207be71f74b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dcc11365-4778-7255-a9e7-5262a1d203e6
---

# SMS_TaskSequence_RegistryConditionExpression Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_RegistryConditionExpression` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a condition expression to check for the existence of a registry key and, optionally, compare it to specified data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_RegistryConditionExpression : SMS_TaskSequence_ConditionExpression
{
      String Data;
      String KeyPath;
      String Operator;
      String Type;
      String Value;
};
```

## Methods

The `SMS_TaskSequence_RegistryConditionExpression` class doesn't define any methods.

## Properties

`Data` Data type: `String`

Access type: Read/Write

Qualifiers: None

User-specified data to compare to the registry key information.

`KeyPath` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

Path for the registry key.

`Operator` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

The condition operator to use in the comparison. Possible values are:

- exists
- nonExists
- equals
- notEquals
- less
- lessEqual
- greater
- greaterEqual

    `Type` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Registry key type. Possible values are:
- REG\_BINARY
- REG\_DWORD
- REG\_EXPAND\_SZ
- REG\_MULTI\_SZ
- REG\_NONE
- REG\_QWORD
- REG\_SZ

    `Value` Data type: `String`

    Access type: Read/Write

    Qualifiers: [AllowedLen("0-250")]

    Value of the registry key. The value length can be between 0 and 250 characters.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

You use `SMS_TaskSequence_RegistryConditionExpression` to check for the existence of a registry key, or alternatively to check for a registry key value. For example, if you have the registry key "HKEY\_LOCAL\_MACHINE\SYSTEM\Select" and the DWORD value set to 'Current' under it, then, `KeyPath` would be "HKEY...\Select", `Operator` would be 'Equals' (or 'NotEquals', and so on), `Type` would be REG\_DWORD, `Value` would be 'Select', and `Data` would be the numeric value to compare against the value of the registry key ('Select').

`Type` applies only when checking for the existence of a registry value specified in `Value`; when comparing values, `Type` isn't used. This means that if 'Exists' is the `Operator` and REG\_SZ is the `Type`, the result will evaluate to `False` because 'Select' is a REG\_DWORD.

However, when comparing values ('Equals', 'Greater', and so on), then `Type` isn't used. Instead the value of `Data` is compared against `Value` regardless of the actual registry type and `Type`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).