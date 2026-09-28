---
layout: Conceptual
title: SMS_AmPolicySummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_ampolicysummary-server-wmi-class
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
description: The SMS_AmPolicySummary Windows Management Instrumentation class is an SMS Provider server class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bc5b4ed0-99ae-e3ea-8d03-f71c23e9dba7
document_version_independent_id: b6474d79-94fa-721d-8dbe-c65fed551cd2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_ampolicysummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_ampolicysummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_ampolicysummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b44e2148-e49f-c7d7-5f47-429d903cb105
---

# SMS_AmPolicySummary Class - Configuration Manager | Microsoft Learn

The `SMS_AmPolicySummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the endpoint protection client antimalware policy status.

Important

This class is only for customized antimalware policy summary.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AmPolicySummary : SMS_BaseClass
{
    UInt32 AppliedCount;
    DateTime AssignmentTime;
    UInt32 ClientSettingsID;
    String CollectionID;
    String CollectionName;
    UInt32 FailureCount;
    UInt32 ID;
    DateTime LastClientUpdateTime;
    UInt32 NotAppliedCount;
    UInt32 TotalCount;
    UInt32 UnknownCount;
};
```

## Methods

The `SMS_AmPolicySummary` class does not define any methods.

## Properties

`AppliedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of clients that applied this particular antimalware policy

`AssignmentTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Local time the customized setting is deployed.

`ClientSettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Unique identifier of the antimalware setting.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Collection identifier.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Collection name.

`FailureCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of clients that failed to apply this particular antimalware policy.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the antimalware setting assignment.

`LastClientUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last update from all assigned clients.

`NotAppliedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of clients that are not applicable to apply the policy.

`TotalCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Total number of clients assigned the policy.

`UnknownCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of unknown clients.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).