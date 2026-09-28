---
layout: Conceptual
title: CCM_Service_GlobalConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class
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
description: Learn how the CCM_Service_GlobalConfiguration class is a client Windows Management Instrumentation (WMI) class that supports global configuration for the CCMEXEC service.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e77fa87f-0c0a-abdc-8133-b7ed1275977e
document_version_independent_id: e817156f-2d72-7515-41e7-635bb99e13f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 135c3ed6-53e8-c776-ea84-e449b1e75ab0
---

# CCM_Service_GlobalConfiguration Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Service_GlobalConfiguration` class is a client Windows Management Instrumentation (WMI) class that supports global configuration for the CCMEXEC service. There's only one instance of this class on a computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_GlobalConfiguration : CCM_Policy
{
      UInt8 Dummy;
      UInt32 EndpointActiveMessageThreshold;
      UInt32 EndpointMessageTimeout;
      UInt32 EndpointReleaseTimeout;
      UInt32 OutgoingMessageTimeout;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String ServiceRootDir;
};
```

## Methods

The `CCM_Service_GlobalConfiguration` class doesn't define any methods.

## Properties

`Dummy` Data type: `UInt8`

Access type: Read/Write

Qualifiers: [Realkey]

Dummy key.

`EndpointActiveMessageThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Default maximum number of outstanding messages that endpoints are allowed. A message is outstanding if it has been dispatched to the endpoint, but the endpoint hasn't called **SetComplete** on the associated context. For serial endpoints, the AMT is always 1. This can be overridden on a per-endpoint basis.

`EndpointMessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Default timeout, in minutes, assigned to all messages that arrive for endpoints. If the value is NULL or 0, no default timeout is assigned. This can be overridden on a per-endpoint basis.

`EndpointReleaseTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Endpoint defaults. The default idle time, in minutes, that endpoints are allowed before they're released by the service. An endpoint is idle when no messages are being dispatched to it. If the value is NULL or 0, endpoints aren't released until the service shuts down. This can be overridden on a per-endpoint basis in the endpoint's configuration.

`OutgoingMessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Service defaults. The default timeout, in minutes, that all messages sent from the computer are assigned. If the value is NULL or 0, no default timeout is assigned. This can be overridden on a per-message basis by using the **Timeout** property of the message.

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

`ServiceRootDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Root directory that the service uses internally for temporary files. The System and Administrators account must have full access to this directory (the latter is to allow the debugging of CCMEXEC as an application). The service creates this directory if it doesn't exist.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).