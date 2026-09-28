---
layout: Conceptual
title: SMS_UserSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_usersettings-server-wmi-class
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
description: The SMS_UserSettings class describes attributes that are specific to a single user that is managed by Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 42905df1-b2d4-771c-cf96-2b51deb7b0be
document_version_independent_id: f45fac43-afab-eadd-b1d2-42139f67b4ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_usersettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_usersettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_usersettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4531e67f-c937-9870-2e7a-48f5e3c35398
---

# SMS_UserSettings Class - Configuration Manager | Microsoft Learn

The `SMS_UserSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes attributes that are specific to a single user that is managed by Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UserSettings
{
      DateTime LastModificationTime;
      UInt32 LocaleID;
      SMS_UserVariable UserVariables[];
      UInt32 ResourceID;
};
```

## Methods

The `SMS_UserSettings` class does not define any methods.

## Properties

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time when the user settings were last modified.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The ID of the locale used to convert the localized name and description of the user. The default locale ID is 1033, English (United States).

`UserVariables` Data type: `SMS_UserVariable` Array

Access type: Read/Write

Qualifiers: [lazy]

The SMS\_UserVariable Server WMI Class objects representing user variables for the user resource.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Key]

The unique resource ID for the user.

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