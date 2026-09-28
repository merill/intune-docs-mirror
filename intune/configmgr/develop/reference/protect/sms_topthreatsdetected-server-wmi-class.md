---
layout: Conceptual
title: SMS_TopThreatsDetected Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_topthreatsdetected-server-wmi-class
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
description: The SMS_TopThreatsDetected class summarizes the top threats found in the last 24 hours per collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2459aab9-fae3-e4fd-8da0-5672060b06ee
document_version_independent_id: 7ee2bb4d-6a4b-bfb5-6e04-0bbd7a17a950
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_topthreatsdetected-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_topthreatsdetected-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_topthreatsdetected-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6081f512-19ac-2ca1-c8c8-8a4707dd1027
---

# SMS_TopThreatsDetected Class - Configuration Manager | Microsoft Learn

The `SMS_TopThreatsDetected` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that summarizes the top threats found in the last 24 hours per collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TopThreatsDetected : SMS_BaseClass
{
    String CollectionID;
    UInt32 MemberCount;
    UInt32 Rank;
    UInt32 ThreatCategoryID;
    UInt64 ThreatID;
    String ThreatName;
    UInt32 TotalMemberCount;
};
```

## Methods

The `SMS_TopThreatsDetected` class does not define any methods.

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier of the collection summarized.

`MemberCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of members with a threat.

`Rank` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Rank of threat exposure in collection (1 is greatest).

`ThreatCategoryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Category identifier of threat. Possible values are:

| CategoryID | Category |
| --- | --- |
| 1 | Adware |
| 2 | Spyware |
| 3 | Password Stealer |
| 4 | Trojan Downloader |
| 5 | Worm |
| 6 | Backdoor |
| 8 | Trojan |
| 9 | Email Flooder |
| 11 | Dialer |
| 12 | Monitoring Software |
| 13 | Browser Modifier |
| 19 | Joke Program |
| 21 | Software Bundler |
| 22 | Trojan Notifier |
| 23 | Settings Modifier |
| 27 | Potentially Unwanted Software |
| 30 | Exploit |
| 32 | Malware Creation Tool |
| 33 | Remote Control Software |
| 34 | Tool |
| 36 | Trojan Denial of Service |
| 37 | Trojan Dropper |
| 38 | Trojan Mass Mailer |
| 39 | Trojan Monitoring Software |
| 40 | Trojan Proxy Server |
| 42 | Virus |
| 43 | Permitted |
| 44 | Not Yet Classified |
| 46 | Suspicious Behavior |

`ThreatID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

Threat identifier.

`ThreatName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the threat.

`TotalMemberCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Total count of members in the collection.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).