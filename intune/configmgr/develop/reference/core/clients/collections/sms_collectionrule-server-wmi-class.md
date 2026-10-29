---
layout: Conceptual
title: SMS_CollectionRule Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class
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
description: Learn how to represent a collection rule using SMS_CollectionRule class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 86a60878-3eea-a95f-989f-bceac4047a8e
document_version_independent_id: 21e2b560-1a09-ed29-b9e4-dfdc3ba99f1a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: bc45345a-1418-a221-7bfb-7f211d1f433f
---

# SMS_CollectionRule Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionRule` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a collection rule in a collection and serves as an abstract base class for [SMS_CollectionRuleDirect Server WMI Class](sms_collectionruledirect-server-wmi-class) and [SMS_CollectionRuleQuery Server WMI Class](sms_collectionrulequery-server-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRule
{
      String RuleName;
};
```

## Methods

The `SMS_CollectionRule` class does not define any methods.

## Properties

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Descriptive name that identifies the rule. The default value is "".

## Remarks

Class qualifiers for this class include:

- Abstract
- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).