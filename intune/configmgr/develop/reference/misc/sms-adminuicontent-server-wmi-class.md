---
layout: Conceptual
title: SMS_AdminUIContent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms-adminuicontent-server-wmi-class
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
description: Learn how to use the SMS_AdminUIContent class although it has no defined methods.
ms.date: 2017-02-15T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
descriptions: Learn about the simplified syntax, methods, properties, and requirements of the SMS_AdminUIContent server class.
locale: en-us
document_id: 78fa373e-5391-97d0-4dae-649f0fddeb5e
document_version_independent_id: 71148322-66a0-8c04-680a-7e99b2b4da13
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms-adminuicontent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms-adminuicontent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms-adminuicontent-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1dd75b04-c5bf-292a-4b82-1ffdd2047e23
---

# SMS_AdminUIContent Class - Configuration Manager | Microsoft Learn

For internal use only.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AdminUIContent : SMS_BaseClass
{
    DateTime CreationDate;
    String Data;
    String Name;
};

```

## Methods

The `SMS_AdminUIContent` class does not define any methods.

## Properties

`CreationDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: None

Reserved for internal use.

`Data` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved for internal use.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [unique, not\_null, key]

Reserved for internal use.

## Remarks

Class qualifiers for this class include:

- Read
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).