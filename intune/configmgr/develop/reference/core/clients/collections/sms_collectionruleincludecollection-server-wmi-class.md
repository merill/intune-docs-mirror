---
layout: Conceptual
title: SMS_CollectionRuleIncludeCollection Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruleincludecollection-server-wmi-class
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
description: An SMS Provider server class that represents an inclusion rule that's added as a rule to the `SMS_Collection` instance.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b7deca36-ccd4-94d6-dc2b-3c15571d8c67
document_version_independent_id: b134986c-32ea-8c44-8fb0-b2c48aa59382
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruleincludecollection-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionruleincludecollection-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionruleincludecollection-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ddf2b320-6a00-2a5c-7077-3afde1e5d456
---

# SMS_CollectionRuleIncludeCollection Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionRuleIncludeCollection` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an inclusion rule that's added as a rule to the `SMS_Collection` instance. Any members of a collection defined by this rule will be included in the collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ CollectionRuleIncludeCollection : SMS_BaseClass
{
      String IncludeCollectionID;
      String RuleName;
};
```

## Methods

The `SMS_ CollectionRuleIncludeCollection` class doesn't define any methods.

## Properties

`IncludeCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the collection to include in the membership results.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CollectionRule Server WMI Class](sms_collectionrule-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).