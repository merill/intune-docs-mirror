---
layout: Conceptual
title: SMS_SIIB_Generic_Configuration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_generic_configuration-server-wmi-class
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
description: Learn how to represent the generic configuration for Configuration Manager components with SMS_SIIB_Generic_Configuration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 51ba4d4d-bf95-6e3b-2050-e6c7c76188d7
document_version_independent_id: ca1abe59-9840-3808-a2c2-2eb8174196ff
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siib_generic_configuration-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siib_generic_configuration-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siib_generic_configuration-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2e7e351d-c3e7-74ea-aada-18dd8633f2db
---

# SMS_SIIB_Generic_Configuration Class - Configuration Manager | Microsoft Learn

The `SMS_SIIB_Generic_Configuration` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents generic configuration for Configuration Manager components.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_Generic_Configuration : SMS_SiteInstallItemBase
{
   String ConfigurationName;
   String ItemName;
   String ItemType;
   SMS_SII_PropertyList PropLists[];
   SMS_SII_Property Props[];
   String Units[];
   String SiteCode;
};
```

## Methods

The `SMS_SIIB_Generic_Configuration` class does not define any methods.

## Properties

`ConfigurationName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the configuration.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`PropLists` Data type: `SMS_SII_PropertyList` Array

Access type: Read-only

Qualifiers: None

[SMS_SII_PropertyList Server WMI Class](sms_sii_propertylist-server-wmi-class) objects for the component.

`Props` Data type: `SMS_SII_Property` Array

Access type: Read-only

Qualifiers: None

[SMS_SII_Property Server WMI Class](sms_sii_property-server-wmi-class) objects for the component.

`Units` Data type: `String` Array

Access type: Read-only

Qualifiers: None

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).