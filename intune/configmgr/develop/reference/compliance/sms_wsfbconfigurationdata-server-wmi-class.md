---
layout: Conceptual
title: SMS_WSfBConfigurationData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_wsfbconfigurationdata-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents Microsoft Store for Business configuration data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d7773411-7e6f-79c0-c0a3-a3e8ad7f3ad7
document_version_independent_id: 024de4e8-8d87-6801-6b90-c483e7b1ce7f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_wsfbconfigurationdata-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_wsfbconfigurationdata-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_wsfbconfigurationdata-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: f1c9763d-af4e-b987-eade-036b61b05879
---

# SMS_WSfBConfigurationData Class - Configuration Manager | Microsoft Learn

The `SMS_WSfBConfigurationData` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Store for Business configuration data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_WSfBConfigurationData : SMS_BaseClass
{
    String ClientId;
    String ContentLocation;
    String DefaultLocale;
    DateTime LastSuccessfulSyncTime;
    SInt32 LastSyncStatus;
    DateTime LastSyncTime;
    String SelectedLocales;
    String TenantId;
};

```

## Methods

The `SMS_WSfBConfigurationData` class does not define any methods.

## Properties

`ClientId` Data type: `String`

Access type: Read

Qualifiers: none

Microsoft Store For Business client ID.

`ContentLocation` Data type: `String`

Access type: Read

Qualifiers: none

Location of the content downloaded from the Microsoft Store For Business.

`DefaultLocale` Data type: `String`

Access type: Read

Qualifiers: none

The default language for the Microsoft Store for Business.

`LastSuccessfulSyncTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The time of the last successful synchronization with Microsoft Store for Business.

`LastSyncStatus` Data type: `SInt32`

Access type: Read

Qualifiers: none

The status of the last synchronization with Microsoft Store for Business.

`LastSyncTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The time of the last synchronization with Microsoft Store for Business.

`SelectedLocales` Data type: `String`

Access type: Read

Qualifiers: none

The selected languages for Microsoft Store for Business.

`TenantId` Data type: `String`

Access type: Read

Qualifiers: [key]

Microsoft Store for Business tenant ID.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).