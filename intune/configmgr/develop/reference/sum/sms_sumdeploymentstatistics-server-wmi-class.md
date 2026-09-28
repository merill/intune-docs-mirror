---
layout: Conceptual
title: SMS_SUMDeploymentStatistics Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_sumdeploymentstatistics-server-wmi-class
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
description: An SMS Provider server class that represents a per-deployment summary for SUM deployments in-console monitoring.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 35968d1d-782c-47a6-fed1-a036b72ef6ee
document_version_independent_id: b68bd052-a820-4b98-38af-0c600b0f7657
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_sumdeploymentstatistics-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_sumdeploymentstatistics-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_sumdeploymentstatistics-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8b3b4bd3-f166-97e4-5572-e6df494efa3d
---

# SMS_SUMDeploymentStatistics Class - Configuration Manager | Microsoft Learn

The `SMS_SUMDeploymentStatistics` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a per-deployment summary for SUM deployments in-console monitoring.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SUMDeploymentStatistics : SMS_BaseClass  
{  
    UInt32 AssignmentID;  
    String AssignmentUniqueID;  
    UInt32 NumError;  
    UInt32 NumInProgress;  
    UInt32 NumReqsNotMet;  
    UInt32 NumSuccess;  
    UInt32 NumUnknown;  
    DateTime SummarizationTime;  
};  
```

## Methods

The `SMS_SUMDeploymentStatistics` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The ID of the configuration item assignment. This ID is unique only for the site.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The unique ID of the configuration item assignment. This ID is unique across sites.

`NumError` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of the number of errors.

`NumInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of the number in progress.

`NumReqsNotMet` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of the number where requirements are not met.

`NumSuccess` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of the number of successes.

`NumUnknown` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of the number unknown.

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Summarization time.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).