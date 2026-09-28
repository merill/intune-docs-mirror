---
layout: Conceptual
title: SMS_TaskSequence_SoftwareConditionExpression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class
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
description: An SMS Provider server class that represents a condition expression to verify if a specified product is installed on the destination computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fa351a0b-30c3-15b0-b77a-6936e2cea5a9
document_version_independent_id: 4c982bbd-f6e7-8738-b1d0-9161e52426fd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_softwareconditionexpression-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 80a5dfc3-027f-99eb-d238-062d588ad7fc
---

# SMS_TaskSequence_SoftwareConditionExpression Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_SoftwareConditionExpression` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a condition expression to verify if a specified product is installed on the destination computer. If the software exists, the action is run; otherwise it is not run.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_SoftwareConditionExpression : SMS_TaskSequence_ConditionExpression
{
      String Operator;
      String ProductCode;
      String ProductName;
      String UpgradeCode;
      String Version
};
```

## Methods

The `SMS_TaskSequence_SoftwareConditionExpression` class does not define any methods.

## Properties

`Operator` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null]

The condition operator to use for the comparison. Possible values are:

- AnyVersion
- ThisVersion

    `ProductCode` Data type: `String`

    Access type: Read/Write

    Qualifiers: [Not\_Null]

    The Windows Installer package product code to be compared.

    `ProductName` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    The product name.

    `UpgradeCode` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    The upgrade code for the product to be compared.

    `Version` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    The version of the software.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Using this condition, you can do the following:

Check for the existence of a specific product.

- `Operator` should be ThisVersion.
- `ProductCode` should the product code.

    Check for existence of a product family.
- `Operator` should be AnyVersion
- `UpgradeCode` should be the upgrade code.

    Either the product code or upgrade code must be specified, otherwise an error will occur.

    The software on the destination computer must be installed using a Windows Installer package for this expression to work. In usage, the class properties are obtained from the Windows Installer package of the software that is to be compared against. For more information, see [Windows Installer](/en-us/windows/desktop/Msi/windows-installer-portal).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).