---
layout: Conceptual
title: SMS_MachineVariable Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_machinevariable-server-wmi-class
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
description: The SMS_MachineVariable WMI class defines the settings of a task sequence variable that is unique to a specific computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3f342829-39b7-78fd-dee4-3d6da6634bb7
document_version_independent_id: 39c784b6-1df5-7b0a-6043-c551ea58d2bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_machinevariable-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_machinevariable-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_machinevariable-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e903d84c-a8e8-e11a-9376-f5a6e275f167
---

# SMS_MachineVariable Class - Configuration Manager | Microsoft Learn

The `SMS_MachineVariable` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that defines the settings of a task sequence variable that is unique to a specific computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MachineVariable
{
      Boolean IsMasked;
      String Name;
      String Value;
};
```

## Methods

The `SMS_MachineVariable` class doesn't define any methods.

## Properties

`IsMasked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

This property isn't currently used.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The name of the machine variable. The default value is "".

`Value` Data type: `String`

Access type: Read/Write

Qualifiers: None

The machine variable value. The default value is `null`.

## Remarks

The task sequence variable can customize the behavior of a task sequence for a specific computer, and it overrides any definition that is set by [SMS_CollectionVariable Server WMI Class](sms_collectionvariable-server-wmi-class). These variables are automatically replicated down through the site hierarchy. For example, if a variable is declared on the primary child site server, it will be available on the primary grandchild site server, but not on the primary site server.

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class to create objects that are embedded by the [SMS_MachineSettings Server WMI Class](sms_machinesettings-server-wmi-class) and accessed by using the `MachineVariables` property. For an example of the use of this class, see How to Create a Computer Variable in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).