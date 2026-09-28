---
layout: Conceptual
title: SMS_FeatureExtension Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_featureextension-server-wmi-class
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
description: Learn how to use the SMS_FeatureExtension class to represent feature extensions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b440afed-070f-3eb8-b948-0c0ffdcadbf1
document_version_independent_id: 465baf40-d454-da26-57bb-a7f042296854
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_featureextension-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_featureextension-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_featureextension-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5159c939-de6b-4ea4-7f9b-993f87572068
---

# SMS_FeatureExtension Class - Configuration Manager | Microsoft Learn

The `SMS_FeatureExtension` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents feature extensions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_FeatureExtension : SMS_BaseClass  
{  
    String FeatureId;  
    String Name;  
    String Description;  
    Boolean IsExposed;  
};  

```

## Methods

The `SMS_FeatureExtension` class does not define any methods.

## Properties

`FeatureId` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The feature ID.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the feature extension.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

A description of the feature extension.

`IsExposed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether the feature extension is exposed.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).