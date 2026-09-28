---
layout: Conceptual
title: SMS_StateMigrationUserNames Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class
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
description: An SMS Provider server class in Configuration Manager that represents a localized username during state migration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2b05fab0-dd9e-4f8f-96bf-1030bb1aba41
document_version_independent_id: 7dc1f301-83ba-50f8-dabf-70e526931e40
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae2c0de0-1db9-5594-9177-352a54b4f301
---

# SMS_StateMigrationUserNames Class - Configuration Manager | Microsoft Learn

The `SMS_StateMigrationUserNames` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents a localized user name during state migration.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StateMigrationUserNames
{
      UInt32 LocaleID;
      String UserName;
};
```

## Methods

The `SMS_StateMigrationUserNames` class doesn't define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the locale associated with the user name.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The localized user name. The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class to create objects that are embedded by the [SMS_StateMigration Server WMI Class](sms_statemigration-server-wmi-class) and accessed using the `UserNames` property. For an example of the use of this class, see How to Create an Association Between Two Computers in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).