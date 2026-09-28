---
layout: Conceptual
title: SMS_CIToContent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that exposes the configuration item to content relationship for a software update.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 72e02e0b-1d93-200f-1835-02b120aa11c4
document_version_independent_id: 530fb2bc-1ac6-e25d-8002-af56e31b51f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_citocontent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a2ffefb9-e8d2-b593-b972-996a8bc3f5c1
---

# SMS_CIToContent Class - Configuration Manager | Microsoft Learn

The `SMS_CIToContent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that exposes the configuration item to content relationship for a software update. It lists all the contents in the configuration item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIToContent : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    String ContentDescription;
    Boolean ContentDownloaded;
    String ContentHash;
    SInt32 ContentHashVersion;
    SInt32 ContentID;
    String ContentLocales[];
    String ContentUniqueID;
    SInt32 ContentVersion;
    String ModelName;
    UInt32 ObjectTypeID;
    String SDMMethodType;
    String SecuredModelName;
};
```

## Methods

The `SMS_CIToContent` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, Not\_null]

Unique ID of the configuration item corresponding to the update. This ID is unique only for the site. The ID is defined by the `CI_ID` property of [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContentDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the update content.

`ContentDownloaded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, Not\_null]

`true` if the content is downloaded; otherwise, `false`.

`ContentHash` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Hash of the content files.

`ContentHashVersion` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The content hash version.

`ContentID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, key, Not\_null]

ID for the software update content.

`ContentLocales` Data type: `String` Array

Access type: Read-only

Qualifiers: [read, Not\_null]

Array of locales associated with the content.

`ContentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

Unique ID of the content.

`ContentVersion` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, Not\_null]

Version of the content.

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, Not\_null]

See [SMS_ObjectContentInfo Server WMI Class](../core/servers/console/sms_objectcontentinfo-server-wmi-class).

`SDMMethodType` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, Not\_null]

System Definition Model (SDM) method type corresponding to the configuration item.

`SecuredModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the secured model.

## Remarks

Class qualifiers for this class include:

- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

    Your application can query this class to get the list of contents and files associated with the software update configuration item. The class can also be used to get the list of configuration items that contain the specified content.

    Software update content must be downloaded manually. To identify the contents to download, your application queries `SMS_CIToContent` and obtains the list of `ContentID` properties matching the specified locale criteria. With this list, the application can obtain the associated download URL and related properties for the content files from [SMS_CIContentFiles Server WMI Class](sms_cicontentfiles-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).