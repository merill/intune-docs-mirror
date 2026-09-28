---
layout: Conceptual
title: SMS_Content Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class
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
description: Learn how the SMS_Content class is an SMS Provider server class, in Configuration Manager, that provides additional information about a CI_Content instance.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0937a214-d7fa-705c-edf2-c812647528df
document_version_independent_id: 902e8a8c-ed63-95b9-4dd0-15e7ebc2e86b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e93f3d5f-c77d-4365-a7fb-c9f2234416c7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/62e8d07a-cc62-4934-b30b-e168a571e51d
platformId: 1ab8281c-c793-3cc9-3e03-b58024b74ab3
---

# SMS_Content Class - Configuration Manager | Microsoft Learn

The `SMS_Content` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides additional information about a `CI_Content` instance.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Content : SMS_BaseClass
{
    String ContentDescription;
    UInt32 ContentFlags;
    String ContentHash;
    UInt32 ContentHashVersion;
    SInt32 ContentID;
    String ContentSource;
    UInt32 ContentType;
    String ContentUniqueID;
    UInt32 ContentVersion;
    UInt32 ObjectTypeID;
    String RelatedContentID;
    String SecurityKey;
};
```

## Methods

The following table lists the methods in the `SMS_Content` class.

| Method | Description |
| --- | --- |
| [IsOfficeContent Method in Class SMS_Content](isofficecontent-method-in-class-sms_content) | Specifies whether content is Microsoft Office content. |

## Properties

`ContentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the content.

`ContentFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This specifies additional attributes for content instance.

| Value | Content flag |
| --- | --- |
| 8 | DOWNLOAD\_ON\_DEMAND\_FROM\_LOCAL\_DP |
| 12 | DOWNLOAD\_FROM\_LOCAL\_DISPPOINT |
| 13 | DOWNLOAD\_LOCAL\_PARTIALDOWNLOADTOLOCAL |
| 14 | DOWNLOAD\_FROM\_REMOTE\_DISPPOINT |
| 15 | DOWNLOAD\_REMOTE\_PARTIALDOWNLOADTOLOCAL |
| 16 | DOWNLOAD\_ENABLE\_PEER\_CACHING |
| 17 | DP\_NO\_FALLBACK\_UNPROTECTED |
| 24 | DO\_NOT\_DOWNLOAD |
| 25 | PERSIST\_IN\_CACHE |

`ContentHash` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Hash of the content.

`ContentHashVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

This specifies the hash version used to calculate the content hash.

`ContentID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifier for the content.

`ContentSource` Data type: `String`

Access type: Read/Write

Qualifiers: none

This specifies the source location where content files are stored.

`ContentType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Type of the content.

`ContentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Unique identifier for the content.

`ContentVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Version of the content.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The security type of the content.

`RelatedContentID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Specifies the related content associated with this content.

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: none

The security key of the content. Content may be secured by application or package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).