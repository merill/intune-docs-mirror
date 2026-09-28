---
layout: Conceptual
title: SMS_ResIDValueLookup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_residvaluelookup-server-wmi-class
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
description: In Configuration Manager, the SMS_ResIDValueLookup WMI class is an SMS Provider server class that maps integers to localized text strings found in a resource DLL.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 51f8b541-6205-cb47-6372-6e2accfda1fa
document_version_independent_id: 10efc9cf-dbfe-b381-01cf-070da8443800
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_residvaluelookup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_residvaluelookup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_residvaluelookup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 17fef469-81d8-2851-6802-2deeb94712a9
---

# SMS_ResIDValueLookup Class - Configuration Manager | Microsoft Learn

The `SMS_ResIDValueLookup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps integers to localized text strings found in a resource DLL.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ResIDValueLookup
{
     String LookupName;
     UInt32 IntLookupValue;
     String StringLookupValue;
     String ResDLL;
     UInt32 ResID;
};
```

## Methods

The `SMS_ResIDValueLookup` class does not define any methods.

## Properties

`LookupName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name specified in the ResIDValueLookup property qualifier.

`IntLookupValue` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Value from the property to be localized. Specify a value for this property if the data type of the property to be localized is an integer. The default value is 0.

`StringLookupValue` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Value from the property to be localized. Specify a value for this property if the data type of the property to be localized is a string. The default value is "".

`ResDLL` Data type: `String`

Access type: Read/Write

Qualifiers: None

Resource DLL name from which to retrieve a localized string. The default value is "".

`ResID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Resource ID from which to retrieve the localized string. The default value is 0.

## Remarks

Class qualifiers for this class include:

- Static

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    The Configuration Manager console uses this class to convert enumerated property values into localized text strings. The console uses the ResIDValueLookup qualifier value and the property value of the class instance to look up the location of the localized string.

    For example, to get the location of the localized string for the `Priority` property of [SMS_Package Server WMI Class](../../servers/configure/sms_package-server-wmi-class), the property must contain a ResIDValueLookup property qualifier:

1. Get the property value.
2. Either query `SMS_ResIDValueLookup` or get the object directly by specifying the full path. The query and the object path are as follows.

    ```
    SELECT * FROM SMS_ResIDValueLookup
    WHERE LookupName = < property qualifier value>
    AND IntLookupValue = <property value>
    
    SMS_ResIDValueLookup.IntLookupValue=<property value>,LookupName="<qualifier value>",StringLookupValue=""
    ```

    When you have the location and resource identifier, you can use the `LoadString` Win32 function to return the localized text string for the Priority value.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).