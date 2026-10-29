---
layout: Conceptual
title: SMS_ClientDeploymentStateDetailsView Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentstatedetailsview-server-wmi-class
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
description: Learn how to represent a clients deployment state using SMS_ClientDeploymentStateDetailsView in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5d49bfe3-126a-38be-62c4-f93ae6a51f82
document_version_independent_id: fd03da53-968d-3b94-6316-06d4b2756474
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentstatedetailsview-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentstatedetailsview-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentstatedetailsview-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: cda119ce-5ce3-cc31-1845-74d0341bfef6
---

# SMS_ClientDeploymentStateDetailsView Class - Configuration Manager | Microsoft Learn

The `SMS_ClientDeploymentStateDetailsView` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment state details view.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDeploymentStateDetailsView: SMS_BaseClass
{
    UInt32 BaselineItemID;
    String BaselineItemName;
    UInt32 BaselineItemType;
    String NetBiosName;
    UInt32 RecordID;
    String SMSID;
};

```

## Methods

The `SMS_ClientDeploymentStateDetailsView` class does not define any methods.

## Properties

`BaselineItemID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The client baseline item ID.

`BaselineItemName` Data type: `String`

Access type: Read

Qualifiers: none

The client baseline item name.

`BaselineItemType` Data type: `UInt32`

Access type: Read

Qualifiers: none

The client baseline item type. Possible values are:

| Value | Baseline item type |
| --- | --- |
| 1 | Patch or CU |
| 2 | Language Pack |

`NetBiosName` Data type: `String`

Access type: Read

Qualifiers: none

The NetBIOS name of the client.

`RecordID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The record ID of the client deployment state.

`SMSID` Data type: `String`

Access type: Read

Qualifiers: none

The SMSID of the client.

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