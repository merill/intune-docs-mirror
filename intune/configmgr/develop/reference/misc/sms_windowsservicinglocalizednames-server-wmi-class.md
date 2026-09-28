---
layout: Conceptual
title: SMS_WindowsServicingLocalizedNames Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_windowsservicinglocalizednames-server-wmi-class
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
description: The SMS_WindowsServicingLocalizedNames Server WMI Class is for internal use only.For more information about both the class qualifiers and the property qualifiers, see Configuration Manager Class and Property Qualifiers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 949a68ea-1416-80a9-d16b-358fdf56eedc
document_version_independent_id: 0aa20392-c4f9-2611-01c7-81a2c07feea5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_windowsservicinglocalizednames-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_windowsservicinglocalizednames-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_windowsservicinglocalizednames-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 26e3ed0d-a6c0-7bf2-007b-28a05f63b647
---

# SMS_WindowsServicingLocalizedNames Class - Configuration Manager | Microsoft Learn

For internal use only.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_WindowsServicingLocalizedNames : SMS_BaseClass
{
    UInt32 LocaleID;
    String Name;
    String Value;
};

```

## Methods

The `SMS_WindowsServicingLocalizedNames` class does not define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read

Qualifiers: [key, not\_null]

Reserved for internal use.

`Name` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

Reserved for internal use.

`Value` Data type: `String`

Access type: Read

Qualifiers: none

Reserved for internal use.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).