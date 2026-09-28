---
layout: Conceptual
title: SMS_MDMAppleVppToken Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents an Apple Volume Purchase Program (VPP) token.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5f64b6a6-13ec-0d74-5081-defa4814241b
document_version_independent_id: 27ba085e-ba72-7b90-9b31-9066c9c69226
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bbe00a0c-e771-1db2-3635-8279b8d99450
---

# SMS_MDMAppleVppToken Class - Configuration Manager | Microsoft Learn

The `SMS_MDMAppleVppToken` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an Apple Volume Purchase Program (VPP) token.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMAppleVppToken : SMS_BaseClass
{
    DateTime Created;
    String Description;
    DateTime ExpirationDate;
    String Id;
    DateTime LastSuccessfulSync;
    DateTime LastSync;
    DateTime LastUpdated;
    String Name;
    String OrganizationName;
    String SyncErrorCode;
    DateTime SyncStartTime;
    SInt32 SyncStatus;
};

```

## Methods

The following table lists the methods in the `SMS_MDMAppleVppToken` class.

| Method | Description |
| --- | --- |
| [SyncToken Method in Class SMS_MDMAppleVppToken](synctoken-method-in-class-sms_mdmapplevpptoken) | Initiates a synchronization of an Apple VPP token. |
| [UploadToken Method in Class SMS_MDMAppleVppToken](uploadtoken-method-in-class-sms_mdmapplevpptoken) | Uploads an Apple VPP token to Intune. |

## Properties

`Created` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date the token was created.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the token.

`ExpirationDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Expiration date of the token.

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The token ID.

`LastSuccessfulSync` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The last time a synchronization with Apple was successful.

`LastSync` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The last time a synchronization with Apple occurred.

`LastUpdated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The last time the token was updated.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the token.

`OrganizationName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Organization name for the token.

`SyncErrorCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Error code for a synchronization error.

`SyncStartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time when a synchronization was initiated.

`SyncStatus` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Status of the current or last synchronization.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).