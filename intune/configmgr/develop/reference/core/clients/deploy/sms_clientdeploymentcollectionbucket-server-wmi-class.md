---
layout: Conceptual
title: SMS_ClientDeploymentCollectionBucket Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentcollectionbucket-server-wmi-class
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
description: The SMS_ClientDeploymentCollectionBucket Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents a client deployment collection bucket.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 450ea17f-1c9b-ea1b-7c4a-bd51cd26474f
document_version_independent_id: 180355d8-d306-25f0-8a98-0ef39a1b40bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentcollectionbucket-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentcollectionbucket-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentcollectionbucket-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4ca95830-11b6-229f-68e4-9f04fbb3f7aa
---

# SMS_ClientDeploymentCollectionBucket Class - Configuration Manager | Microsoft Learn

The `SMS_ClientDeploymentCollectionBucket` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment collection bucket that is used to display the localized name in the client deployment detail view.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDeploymentCollectionBucket: SMS_BaseClass
{
    UInt32 BaselineType;
    String Bucket;
    String CollectionID;
    String CollectionName;
    UInt32 FeatureType;
};

```

## Methods

The `SMS_ClientDeploymentCollectionBucket` class does not define any methods.

## Properties

`BaselineType` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The baseline type. Possible values are:

| Value | Baseline type |
| --- | --- |
| 1 | Product Baseline |
| 2 | Staging Baseline |

`Bucket` Data type: `String`

Access type: Read

Qualifiers: [key]

The client deployment status bucket. Possible values are:

| Value |
| --- |
| CDUnknown |
| CDFullCompliant |
| CDInProgress |
| CDNotCompliant |
| CDCriticalError |

`CollectionID` Data type: `String`

Access type: Read

Qualifiers: [key]

The ID of the collection.

`CollectionName` Data type: `String`

Access type: Read

Qualifiers: none

The name of the collection.

`FeatureType` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The feature type. Possible values are:

| Value | Feature type |
| --- | --- |
| 3 | Client Deployment |

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).