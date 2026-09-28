---
layout: Conceptual
title: SMS_CollectionBucket Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionbucket-server-wmi-class
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
description: Learn how to represent the joining of collection and bucket with the SMS_CollectionBucket class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 741015e7-b1c9-bb8c-b55b-2dc6fb70c1f4
document_version_independent_id: 7a84e50a-604f-3dac-baa6-e57fc77d11ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionbucket-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionbucket-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionbucket-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 128d13ea-1895-d167-140b-d07013058b43
---

# SMS_CollectionBucket Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionBucket` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents joining of collection and bucket. By default, all collections will have a client health related bucket, while the endpoint protection bucket is only applicable to endpoint protection allowed collections.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionBucket : SMS_BaseClass
{
    String Bucket;
    String CollectionID;
    String CollectionName;
    UInt32 FeatureType;
};
```

## Methods

The `SMS_CollectionBucket` class does not define any methods.

## Properties

`Bucket` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Bucket summarized.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier of collection summarized.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of collection summarized.

`FeatureType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of feature type.

| Value | Feature Type |
| --- | --- |
| 1 | EndPoint Protection |
| 2 | Client Check |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).