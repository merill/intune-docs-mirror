---
layout: Conceptual
title: CCM_Scheduler_History Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_history-client-wmi-class
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
description: A client Windows Management Instrumentation class that represents the history for a schedule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5b6d3c76-c1f5-d079-3e6f-6734c011ebd2
document_version_independent_id: fdf4998a-bcdb-f93e-9234-4bab9d42abd2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_history-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_history-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_history-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a8eb089f-fb50-abd0-7687-5bb2ad7a94c4
---

# CCM_Scheduler_History Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Scheduler_History` class is a client Windows Management Instrumentation (WMI) class that represents the history for a schedule.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Scheduler_History {
      String  ScheduleID;
      String  UserSID;
      DateTime  FirstEvalTime;
      DateTime  ActivationMessageSent;
      Boolean  ActivationMessageSentIsGMT;
      DateTime  ExpirationMessageSent;
      Boolean  ExpirationMessageSentIsGMT;
      DateTime  LastTriggerTime;
      String  TriggerState;
};
```

## Properties

`ScheduleID` Data type: `String`

Access type: Read-only

Qualifiers: [Not\_Null:ToInstance, Key]

ID of the schedule to which this history item refers.

`UserSID` Data type: `String`

Access type: Read-only

Qualifiers: [Not\_Null:ToInstance, Key]

User owning the schedule.

`FirstEvalTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [Not\_Null:ToInstance, Key]

Date and time when the schedule was first evaluated by the scheduler.

`ActivationMessageSent` Data type: `DateTime`

Access type: Read-only

Qualifiers: None

Last time the activation message was sent for the schedule.

`ActivationMessageSentIsGMT` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the time indicated by `ActivationMessageSent` is in Universal Coordinated Time (UTC).

`ExpirationMessageSent` Data type: `DateTime`

Access type: Read-only

Qualifiers: None

Last date and time when the expiration message was sent for the schedule.

`ExpirationMessageSentIsGMT` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the time indicated by `ExpirationMessageSent` is in Universal Coordinated Time (UTC).

`LastTriggerTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: None

Last date and time when a trigger on the schedule fired. A NULL value indicates that a trigger has not yet fired on the schedule.

`TriggerState` Data type: `String`

Access type: Read-only

Qualifiers: None

State information that individual triggers can set and query.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).