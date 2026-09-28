---
layout: Conceptual
title: CCM_Scheduler_ScheduledMessage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_scheduledmessage-client-wmi-class
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
description: A client Windows Management Instrumentation class that represents the configuration for a scheduled message.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 571c3fe8-daeb-b1f5-6479-cd187e69d05f
document_version_independent_id: 216a8c7e-d41c-c94c-e692-111055af9ae3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_scheduledmessage-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_scheduledmessage-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_scheduler_scheduledmessage-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a0e9a4b6-e68b-74af-9c6f-ab87109a410f
---

# CCM_Scheduler_ScheduledMessage Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Scheduler_ScheduledMessage` class is a client Windows Management Instrumentation (WMI) class that represents the configuration for a scheduled message. There is an instance of this class for each scheduled message.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Scheduler_ScheduledMessage : CCM_Policy
{
      String ActiveMessage;
      DateTime ActiveTime;
      Boolean ActiveTimeIsGMT;
      UInt32 DeadlineMinutes;
      String DeliverMode;
      String ExpireMessage;
      DateTime ExpireTime;
      Boolean ExpireTimeIsGMT;
      UInt32 LaunchConditions;
      String MessageName;
      String MessageTimeout;
      UInt32 Order;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String ReplyToEndpoint;
      String ScheduledMessageID;
      String TargetEndpoint;
      String TriggerMessage;
      String Triggers[];
};
```

## Methods

The `CCM_Scheduler_ScheduledMessage` class does not define any methods.

## Properties

`ActiveMessage` Data type: `String`

Access type: Read/Write

Qualifiers: None

Message to send when the schedule becomes active. If the value is omitted, no message is sent to the target endpoint.

`ActiveTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the schedule becomes active.

`ActiveTimeIsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if ActiveTime is in Universal Coordinated Time (UTC). If the value is omitted or set to FALSE, the time specifies the client computer's local time.

`DeadlineMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Defines how long the schedule will be on hold if its launch conditions are not met. The default value is 4320 minutes (3 days).

`DeliverMode` Data type: `String`

Access type: Read/Write

Qualifiers: None

Mode set for every message delivered under the schedule. Possible values are:

- Express
- Recoverable

    `ExpireMessage` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Message to send when the schedule expires. If the value is omitted, no message is sent to the target endpoint.

    `ExpireTime` Data type: `DateTime`

    Access type: Read/Write

    Qualifiers: None

    Date and time when the schedule expires.

    `ExpireTimeIsGMT` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: None

    `true` if `ExpireTime` is in Universal Coordinated Time (UTC). If the value is omitted or set to `false`, the time specifies the client computer's local time.

    `LaunchConditions` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Defines the system resource conditions to fire this schedule. The default value is 1. Possible values are a combination of the following:

| Value | Launch Condition type |
| --- | --- |
| 0 | eTaskCondition\_None |
| 1 | eTaskCondition\_AboveCriticalBattery |
| 2 | eTaskCondition\_AboveLowBattery |
| 4 | eTaskCondition\_OnAC |
| 8 | eTaskCondition\_Idle |
| 16 | eTaskCondition\_NetworkConnected |

Important

Only one of these power conditions should be supplied in the schedule policy. If more than one is supplied, we honor:

OnAC &gt; AboveLowBattery &gt; AboveCriticalBattery

`MessageName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name to set for every message delivered under the schedule. If the value is omitted, this property is not set on the message.

`MessageTimeout` Data type: `String`

Access type: Read/Write

Qualifiers: None

Timeout set for every message delivered under the schedule. If the value is omitted or set to 0, the timeout is set to INFINITE.

`Order` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Defines the order of the firing if multiple schedules were waiting on conditions and now all the conditions have been met. The smaller the number, the higher the priority. The default value is 4294967295 (0xFFFFFFFF).

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`ReplyToEndpoint` Data type: `String`

Access type: Read/Write

Qualifiers: None

Reply-to endpoint set for every message delivered under the schedule. If the value is omitted, this property is not set on the message.

`ScheduledMessageID` Data type: `String`

Access type: Read/Write

Qualifier: [RealKey, Not\_Null]

ID of the scheduled message, which can be any unique string.

`TargetEndpoint` Data type: `String`

Access type: Read/Write

Qualifiers: None

Endpoint address to send messages to when a trigger fires or when activation/expiration occurs. This address is relative to the computer on which the scheduler evaluates the schedule.

`TriggerMessage` Data type: `String`

Access type: Read/Write

Qualifiers: None

Message to send when a trigger on the schedule occurs. If the value is omitted, an empty message is sent to the target endpoint.

`Triggers` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Array of trigger strings that define when the message should be sent.

### Syntax

```

<TriggerString> := <TriggerType> [ ';' <Name> '=' <Value>]*

<TriggerType> :=  The type of  trigger.
<Name> := Name of a property defined by the trigger type.
<Value> := Value of the property.
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).