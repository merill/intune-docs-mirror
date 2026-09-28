---
layout: Conceptual
title: SMS_UpdateComplianceStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatecompliancestatus-server-wmi-class
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
description: Learn how to represent the client computer compliance status for software updates using SMS_UpdateComplianceStatus class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3fd2e20f-440b-c2a0-8a1c-4df6fa8aaded
document_version_independent_id: 9f8d7b2e-eb82-fa00-0043-2aaebd63d529
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_updatecompliancestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_updatecompliancestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_updatecompliancestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54cbc1ba-a263-858e-8c8f-71a0b3ef6da3
---

# SMS_UpdateComplianceStatus Class - Configuration Manager | Microsoft Learn

The `SMS_UpdateComplianceStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the client computer compliance status for software updates.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UpdateComplianceStatus : SMS_BaseClass  
{  
      String ArticleID;  
      String BulletinID;  
      UInt32 CI_ID;  
      UInt32 EnforcementSource;  
      UInt32 LastEnforcementMessageID;  
      String LastEnforcementMessageName;  
      DateTime LastEnforcementMessageTime;  
      UInt32 LastEnforcementStatusMsgID;  
      DateTime LastStatusChangeTime;  
      DateTime LastStatusCheckTime;  
      String LocalizedDescription;  
      String LocalizedDisplayName;  
      String LocalizedInformativeURL;  
      UInt32 MachineID;  
      UInt32 Status;  
      String UpdateLocales;  
};  
```

## Methods

The `SMS_UpdateComplianceStatus` class does not define any methods.

## Properties

`ArticleID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Knowledge base article ID for the software update.

`BulletinID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Bulletin ID for security updates released by Microsoft.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The ID of the software update configuration item. This ID is not unique across sites.

`EnforcementSource` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Source of the compliance enforcement action. Possible values are:

| Value | Source |
| --- | --- |
| 0 | NONE |
| 1 | SMS |
| 2 | USER |

`LastEnforcementMessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The ID of the last enforcement state message received.

`LastEnforcementMessageName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the last enforcement state message.

`LastEnforcementMessageTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time of the last enforcement state message.

`LastEnforcementStatusMsgID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The ID of the last enforcement status message received.

`LastStatusChangeTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time of the last compliance status change.

`LastStatusCheckTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The date and time of the last compliance status check.

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Localized description of the configuration item.

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Localized display name of the configuration item.

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

URL for additional localized information about the configuration item.

`MachineID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, key, not\_null]

The ID of the target computer.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

The status of the target computer. Possible values are:

| Value | Status |
| --- | --- |
| 0 | Detection state unknown |
| 1 | Update is not required |
| 2 | Update is required |
| 3 | Update is installed |

`UpdateLocales` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Update locales.

## Remarks

Class qualifiers for this class include:

- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    See About Configuration Baselines and Configuration Items for a discussion of compliance.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).