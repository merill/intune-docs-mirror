---
layout: Conceptual
title: SMS_UpdateDeploymentSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatedeploymentsummary-server-wmi-class
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
description: Learn how to represent a summary for a given software update in given software updates deployment in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8e074401-958e-b58b-a150-34779e6f6b5d
document_version_independent_id: 9ab8710f-bf35-b9f8-b010-e5ac9f7fcff9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_updatedeploymentsummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_updatedeploymentsummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_updatedeploymentsummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ed37b46f-80c8-9d21-866e-f913151ed992
---

# SMS_UpdateDeploymentSummary Class - Configuration Manager | Microsoft Learn

The `SMS_UpdateDeploymentSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a summary for a given software update in given software updates deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UpdateDeploymentSummary : SMS_BaseClass  
{  
      Boolean AssignmentEnabled;  
      UInt32 AssignmentID;  
      String AssignmentName;  
      String AssignmentUniqueID;  
      UInt32 CI_ID;  
      String CollectionID;  
      String CollectionName;  
      Boolean IncludeSubCollections;  
      UInt32 NumFailed;  
      UInt32 NumInstalled;  
      UInt32 NumMissing;  
      UInt32 NumNotApplicable;  
      UInt32 NumPresent;  
      UInt32 NumTotal;  
      UInt32 NumUnknown;  
      DateTime StartTime;  
};  
```

## Methods

The `SMS_UpdateDeploymentSummary` class does not define any methods.

## Properties

`AssignmentEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the assignment is enabled.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The ID for the configuration item assignment.

`AssignmentName` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The name of the configuration item assignment.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The unique ID of the configuration item assignment.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The ID of the software update configuration item. This ID is only unique for the site.

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The ID for the collection associated with the update deployment.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The name of the collection associated with the update deployment.

`IncludeSubCollections` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

This property is deprecated in Configuration Manager.

`NumFailed` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the configuration item installation failed.

`NumInstalled` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the configuration item was installed by enforcement.

`NumMissing` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the configuration item is missing.

`NumNotApplicable` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the configuration item is not applicable.

`NumPresent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the configuration item is already installed.

`NumTotal` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Total number of computers in the collection.

`NumUnknown` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

Number of computers for which the state of the configuration item is unknown.

`StartTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time when the assignment was initially offered.

## Remarks

Class qualifiers for this class include:

- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).