---
layout: Conceptual
title: SMS_MachineSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_machinesettings-server-wmi-class
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
description: The SMS_MachineSettings WMI class describes attributes that are specific to a single computer that is managed by Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f07d74e8-48c4-426c-17b5-1eeacd101f29
document_version_independent_id: c466577c-bae8-9d23-73f1-61b6e55b34db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_machinesettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_machinesettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_machinesettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: da3eb471-5069-5622-323e-7c2672778b66
---

# SMS_MachineSettings Class - Configuration Manager | Microsoft Learn

The `SMS_MachineSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes attributes that are specific to a single computer that is managed by Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MachineSettings
{
      DateTime LastModificationTime;
      UInt32 LocaleID;
      SMS_MachineVariable MachineVariables[];
      UInt32 ResourceID;
      String SourceSite;
};
```

## Methods

The `SMS_MachineSettings` class does not define any methods.

## Properties

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time when the computer settings were last modified.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The ID of the locale used to convert the localized name and description of the computer. The default locale ID is 1033, English (United States).

`MachineVariables` Data type: `SMS_MachineVariable` Array

Access type: Read/Write

Qualifiers: [lazy]

The [SMS_MachineVariable Server WMI Class](sms_machinevariable-server-wmi-class) objects representing computer variables for the computer resource.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Key]

The unique resource ID for the computer.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3"), Not\_null]

The code of the source site. The code length can be up to three characters. The default value is "".

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application can use this class as described in How to Create a Computer Variable in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).