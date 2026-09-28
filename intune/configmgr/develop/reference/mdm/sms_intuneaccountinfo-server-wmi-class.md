---
layout: Conceptual
title: SMS_IntuneAccountInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_intuneaccountinfo-server-wmi-class
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
description: In Configuration Manager, the SMS_IntuneAccountInfo WMI class is an SMS Provider server class that represents Microsoft Intune account information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f59a5c76-c16e-aaa7-0d27-5243d9b38072
document_version_independent_id: 1796a43d-52ac-5e1e-3f00-278d7eaf7726
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_intuneaccountinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_intuneaccountinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_intuneaccountinfo-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c82ff960-489e-da10-7797-cc122f095590
---

# SMS_IntuneAccountInfo Class - Configuration Manager | Microsoft Learn

The `SMS_IntuneAccountInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Intune account information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_IntuneAccountInfo : SMS_BaseClass
{
    String AADTenantID;
    String IntuneAccountID;
    Datetime LastUpdateTime;
};

```

## Methods

The `SMS_IntuneAccountInfo` class does not define any methods.

## Properties

`AADTenantID` Data type: `String`

Access type: Read

Qualifiers: none

The GUID of the Microsoft Entra account.

`IntuneAccountID` Data type: `String`

Access type: Read

Qualifiers: [key]

The GUID of the Microsoft Intune account.

`LastUpdateTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The last date and time that the account was updated.

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