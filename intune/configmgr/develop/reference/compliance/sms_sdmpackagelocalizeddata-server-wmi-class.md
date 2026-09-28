---
layout: Conceptual
title: SMS_SDMPackageLocalizedData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_sdmpackagelocalizeddata-server-wmi-class
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
description: In Configuration Manager, the SMS_SDMPackageLocalizedData Windows Management Instrumentation class is an SMS Provider server class that represents localized data for a System Definition Model package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 24ebf92a-a2ef-272f-db7c-8824fb3c0f46
document_version_independent_id: 88eee9d0-2644-feb2-b406-a4a3577b61a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_sdmpackagelocalizeddata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_sdmpackagelocalizeddata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_sdmpackagelocalizeddata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2fc6d52c-cc58-f4be-2a48-fdc2f64f7fd8
---

# SMS_SDMPackageLocalizedData Class - Configuration Manager | Microsoft Learn

The `SMS_SDMPackageLocalizedData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents localized data for a System Definition Model (SDM) package.

## Syntax

```
Class SMS_SDMPackageLocalizedData
{
      UInt32 LocaleID;
      String LocalizedData;
};
```

## Methods

The `SMS_SDMPackageLocalizedData` class does not define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The ID of the locale associated with the localized information.

`LocalizedData` Data type: `String`

Access type: Read/Write

Qualifiers: None

The localized data.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is embedded by the [SMS_ConfigurationItemBaseClass Server WMI Class](sms_configurationitembaseclass-server-wmi-class) through the `SDMPackageLocalizedData` property.

    The application uses this class to add localized string resources to the server database.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).