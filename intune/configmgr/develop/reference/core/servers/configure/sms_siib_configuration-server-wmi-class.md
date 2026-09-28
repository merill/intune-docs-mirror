---
layout: Conceptual
title: SMS_SIIB_Configuration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_configuration-server-wmi-class
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
description: The SMS_SIIB_Configuration WMI class is an SMS Provider server class, in Configuration Manager, that represents the configuration in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6d348657-4d5e-2fd7-3af1-28368647f921
document_version_independent_id: 75b931ab-5301-d438-01cb-54ef6a592186
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siib_configuration-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siib_configuration-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siib_configuration-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e832ec43-945c-522d-43b9-89483a5d1766
---

# SMS_SIIB_Configuration Class - Configuration Manager | Microsoft Learn

The `SMS_SIIB_Configuration` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the configuration for a property page in the Configuration Manager console.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_Configuration : SMS_SiteInstallItemBase
{
   String ChmFile;
   String ConfigUnitName;
   String ConfigurationName;
   UInt32  DescriptionID;
   UInt32  DispIconID;
   UInt32  DispNameID;
   UInt32  Flags;
   String GUID;
   String HtmFile;
   String ItemName;
   String ItemType;
   String ResDLL;
   String SiteCode;
   String Type;
   String Units[];
};
```

## Methods

The `SMS_SIIB_Configuration` class does not define any methods.

## Properties

`ChmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`ConfigUnitName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the configuration unit to find in the site control file.

`ConfigurationName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the configuration.

`DescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`DispIconID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`DispNameID` Data type: `UInt32`

Access type: Read-only

This property is deprecated.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: [bits]

Flags defining the site to which the configuration applies. Possible values are listed below. The default value is 3.

0 SECONDARY

1 PRIMARY

`GUID` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`HtmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`ResDLL` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`Type` Data type: `String`

Access type: Read-only

Qualifiers: None

The configuration type. Possible values are:

- COMPONENT\_CONFIGURATION(Component Configuration)
- DISCOVERY\_METHOD(Discovery Method)
- CLIENT\_SETUP\_METHOD(Client Setup Method)
- INVENTORY\_METHOD(Inventory Method)
- CLIENT\_AGENT(Client Agent)
- CLIENT\_ACCOUNT\_CONFIGURATION(Client Account Configuration)
- SERVER\_ACCOUNT\_CONFIGURATION(Server Account Configuration)

    `Units` Data type: `String` Array

    Access type: Read-only

    Qualifiers: None

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