---
layout: Conceptual
title: CCM_Messaging_Configuration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_messaging_configuration-client-wmi-class
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
description: In Configuration Manager, the CCM_Messaging_Configuration class is a client WMI class that supports messaging-related settings that are exposed to administrators.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 750965ef-2d9f-ad0a-6e7f-1260d35d481b
document_version_independent_id: 97582e03-664d-7840-167f-3cd61bc2d056
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_messaging_configuration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_messaging_configuration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_messaging_configuration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b99c8b8-8410-8ad0-3a1b-0b66ebb53300
---

# CCM_Messaging_Configuration Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Messaging_Configuration` class is a client Windows Management Instrumentation (WMI) class that supports messaging-related settings that are exposed to administrators.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Messaging_Configuration : CCM_Policy
{
      UInt8 DummyKey;
      String MessageRetrySpec;
      UInt32 MessageSizeThreshold;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Messaging_Configuration` class does not define any methods.

## Properties

`DummyKey` Data type: `UInt8`

Access type: Read/Write

Qualifiers: [RealKey]

Dummy key.

`MessageRetrySpec` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional field that specifies a list of retry intervals, in minutes. The messaging system uses this when an outgoing message has to be retried. The format of this field is a semicolon-delimited list of integers, such as 1;5;30;60. In the previous example, if a message cannot be delivered due to a transient error, it is retried after 1 minute, then 5 minutes, then 30 minutes, and finally 60 minutes; until the message times out or is successfully delivered. All subsequent retries use the last value in the list (60 minutes in this example). If this field is omitted or incorrectly formatted, the service falls back to using internally hard coded defaults.

`MessageSizeThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Maximum allowed size of messages, in kilobytes. If a message exceeds this threshold and BITS is enabled and the message is transferred using BITS, otherwise the message is transferred using HTTP.

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

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).