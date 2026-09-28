---
layout: Conceptual
title: SMS_CIContentFiles Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class
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
description: In Configuration Manager, the SMS_CIContentFiles Windows Management Instrumentation class is an SMS Provider server class that lists all files associated with the content of a specific SMS_SoftwareUpdate Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0856bc67-9837-426a-c5cc-8ab8e042ca8b
document_version_independent_id: 56d723c9-0c2b-cfca-7eca-325d782e8014
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: caadbca8-6694-e639-d02c-a32b315bb231
---

# SMS_CIContentFiles Class - Configuration Manager | Microsoft Learn

The `SMS_CIContentFiles` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists all files associated with the content of a specific [SMS_SoftwareUpdate Server WMI Class](sms_softwareupdate-server-wmi-class) object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIContentFiles : SMS_BaseClass
{
    String CI_UniqueID;
    UInt32 ContentID;
    String FileHash;
    String FileName;
    SInt64 FileSize;
    String FileVersion;
    String ImportPath;
    Boolean IsSigned;
    UInt32 LanguageID;
    String ModelName;
    UInt32 ObjectTypeID;
    String SourceURL;
};
```

## Methods

The `SMS_CIContentFiles` class does not define any methods.

## Properties

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, Not\_null]

ID for the software update content. See the `ContentID` property of [SMS_CIToContent Server WMI Class](sms_citocontent-server-wmi-class).

`FileHash` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

The file hash.

`FileName` Data type: `String`

Access type: Read-only

Qualifiers: [read, key, Not\_null]

File name, including the subdirectory path under the root directory.

`FileSize` Data type: `SInt64`

Access type: Read-only

Qualifiers: [read, Not\_null]

The size of the file.

`FileVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

The file version.

`ImportPath` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

The file location (including file name) relative to the import root.

`IsSigned` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, Not\_null]

`true` if the software update content is signed.

`LanguageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The language attribute of the file.

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, Not\_null]

Secured object class ID. Possible values are listed below.

| ID value | Object type |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`SourceURL` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

URL where the source for the content file is located.

## Remarks

Class qualifiers for this class include:

- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is used to determine update files to download for a particular update, for example, when there are different locales associated with the update. When using this class, first identify which contents need to be downloaded by querying [SMS_CIToContent Server WMI Class](sms_citocontent-server-wmi-class) and obtain the list of `ContentID` properties matching the specific language criteria. Given the list, you can then obtain the associated download URL and the related properties for the content files from `SMS_CIContentFiles`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).