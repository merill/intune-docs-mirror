---
layout: Conceptual
title: SMS_CI_LocalizedProperties Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ci_localizedproperties-server-wmi-class
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
description: Learn how to use the SMS_CI_LocalizedProperties class in Configuration Manager that contains the localized properties for a configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7ffcb555-5b67-7c4b-25a2-03e76dd64d93
document_version_independent_id: 8f4afcb9-7adb-b319-185c-f31a950a78a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_ci_localizedproperties-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_ci_localizedproperties-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_ci_localizedproperties-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36ce4e47-7558-4508-0813-5b41e8741f4b
---

# SMS_CI_LocalizedProperties Class - Configuration Manager | Microsoft Learn

The `SMS_CI_LocalizedProperties` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains the localized properties for a configuration item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CI_LocalizedProperties
{
      String Description;
      String DisplayName;
      String InformativeURL;
      UInt32 LocaleID;
};
```

## Methods

The `SMS_CI_LocalizedProperties` class doesn't define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the configuration item. The default value is "".

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Display name for the configuration item. The default value is "".

`InformativeURL` Data type: `String`

Access type: Read/Write

Qualifiers: None

URL identifying additional information about the configuration item. The default value is "".

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the locale associated with the localized properties for the configuration item.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is embedded by the following classes, through the `LocalizedInformation` property:
- [SMS_ConfigurationItem Server WMI Class](sms_configurationitem-server-wmi-class)
- [SMS_Driver Server WMI Class](../osd/sms_driver-server-wmi-class)
- [SMS_SoftwareUpdate Server WMI Class](../sum/sms_softwareupdate-server-wmi-class)
- [SMS_AuthorizationList Server WMI Class](../sum/sms_authorizationlist-server-wmi-class)

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).