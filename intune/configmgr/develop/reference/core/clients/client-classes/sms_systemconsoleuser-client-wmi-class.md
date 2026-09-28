---
layout: Conceptual
title: SMS_SystemConsoleUser Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleuser-client-wmi-class
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
description: The SMS_SystemConsoleUser class is a client Windows Management Instrumentation class, in Configuration Manager, that defines usage data about users, based on the Windows security event log.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4ebd2da6-14c9-28d1-9ffc-3805a922846c
document_version_independent_id: 1b27e094-69d9-2ce0-2fa2-320543c4f277
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleuser-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleuser-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_systemconsoleuser-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
platformId: 219f3655-e0f5-e614-e5a2-ceb366cadb97
---

# SMS_SystemConsoleUser Class - Configuration Manager | Microsoft Learn

The `SMS_SystemConsoleUser` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that defines usage data about users, based on the Windows security event log.

Note

For this class to gather usable data, the Auditing of Logon/Logoff policy must be turned on for each computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SystemConsoleUser
{
      DateTime LastConsoleUse;
      UInt32 NumberOfConsoleLogons;
      String SystemConsoleUser;
      UInt32 TotalUserConsoleMinutes;
};
```

## Methods

The `SMS_SystemConsoleUser` class does not define any methods.

## Properties

`LastConsoleUse` Data type: `DateTime`

Access type: Read only

Qualifiers: None

The last date and time when the user logged off from the console.

`NumberOfConsoleLogons` Data type: `UInt32`

Access type: Read only

Qualifiers: None

The total number of logons recorded in the system security event log for the specific user.

`SystemConsoleUser` Data type: `String`

Access type: Read only

Qualifiers: [key]

The user name for the user logged on to the console.

`TotalUserConsoleMinutes` Data type: `UInt32`

Access type: Read only

Qualifiers: None

The total number of console logon minutes recorded in the system security event log for the user.

## Remarks

This class gathers information about a specific user from the system security event log by using logon and logoff events. When a logon event is found, the associated logon ID is used to search for a matching logoff event. If more than one logoff event is found for a specific logon, then the last logoff event is used to calculate the amount of time that the user was logged on. This is because it is possible to issue more than one logoff request before the system actually performs the logoff action. If a matching logoff event cannot be found, the next shutdown event or logon event is used in place of a logoff event. If none of these can be found, the latest entry in the security log is used.

Note

Only interactive logons are acknowledged by this class.

Some security logs can roll over frequently, or they can extend for several years. The time polled for this class is limited to the last 90 days.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).