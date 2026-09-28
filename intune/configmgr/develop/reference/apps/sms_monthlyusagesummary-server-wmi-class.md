---
layout: Conceptual
title: SMS_MonthlyUsageSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class
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
description: The SMS_MonthlyUsageSummary WMI class is an SMS Provider server class that represents a monthly usage summary for a particular file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1186a92f-eeb6-2272-8ab8-14a5db179c99
document_version_independent_id: f9791ced-f65b-dd5a-8582-966c6607cee3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a7f151b9-6021-ac2a-cd74-ec114a166a10
---

# SMS_MonthlyUsageSummary Class - Configuration Manager | Microsoft Learn

The `SMS_MonthlyUsageSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a monthly usage summary for a particular file.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MonthlyUsageSummary : SMS_BaseClass
{
      SInt64 FileID;
      DateTime LastUsage;
      UInt32 MeteredUserID;
      UInt32 ResourceID;
      UInt32 TimeKey;
      UInt32 TSUsageCount;
      UInt32 UsageCount;
      UInt32 UsageTime;
};
```

## Methods

The `SMS_MonthlyUsageSummary` class does not define any methods.

## Properties

`FileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: [key]

File ID for the summarized file.

`LastUsage` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the metered file was last used during the month.

`MeteredUserID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the user of the metered file. This matches the `MeteredUserID` property in [SMS_MeteredUser Server WMI Class](sms_metereduser-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the computer using the metered file. This ID matches the `ResourceId` property in [SMS_R_System Server WMI Class](../core/clients/manage/sms_r_system-server-wmi-class).

`TimeKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Month that the summary data represents, encoded as an integer Year\*100+Month. This property also matches the time key in the [SMS_SummarizationInterval Server WMI Class](sms_summarizationinterval-server-wmi-class) class.

`TSUsageCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Number of times that the summarized file was used under a Terminal Services session during the month.

`UsageCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Number of times that the summarized file was used in a console session during the month.

`UsageTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total amount of time, in seconds, that the summarized file was used during the month.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class compiles data about a file running on a particular computer by a particular user during a calendar month. `TSUsageCount` and `UsageCount` represent the number of times the summarized file was used during a month. For example, a file could have been opened in the month of May and terminated in June. In this case, both May and June have a usage count of 1 for this file although it was only started in May.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).