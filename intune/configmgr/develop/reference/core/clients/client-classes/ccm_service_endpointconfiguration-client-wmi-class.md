---
layout: Conceptual
title: CCM_Service_EndpointConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_endpointconfiguration-client-wmi-class
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
description: Article outlining the use of CCM_Service_EndpointConfiguration class that supports endpoint configuration for the CCMEXEC service.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b47845b1-1bc9-4f6a-a34e-c36ebca8c877
document_version_independent_id: 7dca9ff0-3c94-9da9-b491-5ba7c9a1e93a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_endpointconfiguration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_service_endpointconfiguration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_endpointconfiguration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cb35ee9a-5a65-570f-dea5-ea20b93f4914
---

# CCM_Service_EndpointConfiguration Class - Configuration Manager | Microsoft Learn

Important

This class supports the Configuration Manager 2007 infrastructure; any access to this class or class properties should be read-only.

in Configuration Manager, the `CCM_Service_EndpointConfiguration` class is a client Windows Management Instrumentation (WMI) class that supports endpoint configuration for the CCMEXEC service. There's an instance of this class for each endpoint on the computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_EndpointConfiguration : CCM_Policy
{
      String ACL;
      UInt32 ActiveMessageThreshold;
      String CoClass;
      String Concurrency;
      String DisplayName;
      Boolean ManualStart;
      UInt32 MessageTimeout;
      String Name;
      String NotificationQueries[];
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      UInt32 ReleaseTimeout;
      String ThreadType;
      String Visibility;
};
```

## Methods

The `CCM_Service_EndpointConfiguration` class doesn't define any methods.

## Properties

`ACL` Data type: `String`

Access type: Read/Write

Qualifiers: None

Value indicating the management point. This value might be null, empty, A (for an assigned management point), L (for a local management point), or AL (for both). This is an optional parameter.

`ActiveMessageThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The number of messages that can be processed concurrently in a parallel endpoint.

`CoClass` Data type: `String`

Access type: Read/Write

Qualifiers: None

`ClassID` or `ProgID` of the COM class that implements the endpoint. This is a required field.

`Concurrency` Data type: `String`

Access type: Read/Write

Qualifiers: None

Concurrency level of the endpoint.

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Display name of the endpoint for when it's displayed in a user interface. This is an optional field.

`ManualStart` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Flag indicating whether the delivery of messages should be started manually. If this flag is set, the service won't dispatch messages to the endpoint until it's explicitly started by using the **StartEndpoint** system command.

`MessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Optional. Message timeout, in minutes.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [Realkey]

Name of the endpoint that is used for addressing. This is a required field and must be unique for the computer.

`NotificationQueries` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Array of notification queries (optional parameter).

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

`ReleaseTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Optional. Release timeout, in minutes.

`ThreadType` Data type: `String`

Access type: Read/Write

Qualifiers: None

Thread type on which the endpoint should be invoked.

`Visibility` Data type: `String`

Access type: Read/Write

Qualifiers: None

Flag indicating that the endpoint is public. Public endpoints can receive messages from remote computers. Possible values are:

internal - No remote messages.

signed - Remote messages must be signed by a management point in mixed or native mode. Used on some client endpoints that receive replies from a management point.

clientsigned -Remote messages must be signed by a client in native mode. Used on some management point endpoints.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).