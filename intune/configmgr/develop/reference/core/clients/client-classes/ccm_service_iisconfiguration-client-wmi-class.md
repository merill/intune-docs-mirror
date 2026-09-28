---
layout: Conceptual
title: CCM_Service_IISConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class
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
description: In Configuration Manager, the CCM_Service_IISConfiguration class is a client Windows Management Instrumentation class that supports Internet Information Services-related settings used by CCMEXEC for staging and receiving message payloads on a Management Point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c503cdd7-375a-f7f1-acb0-4dfff125579c
document_version_independent_id: ad73648c-f3ce-5f87-9ea8-b19678abeced
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c816b718-ecb8-2436-7142-d681608eb3c1
---

# CCM_Service_IISConfiguration Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Service_IISConfiguration` class is a client Windows Management Instrumentation (WMI) class that supports Internet Information Services (IIS)-related settings used by CCMEXEC for staging and receiving message payloads on a Management Point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_IISConfiguration : CCM_Policy
{
      UInt8 Dummy[key]  ;
      String IncomingPayloadDir;
      String IncomingPayloadVirtualDir;
      String OutgoingPayloadDir;
      String OutgoingPayloadVirtualDir;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Service_IISConfiguration` class does not define any methods.

## Properties

`Dummy[key]` Data type: `UInt8`

Access type: Read/Write

Qualifiers: [Realkey]

Dummy key.

`IncomingPayloadDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory where message payloads are uploaded to the server by clients. The System and Administrators account must have full access to this directory. In addition, the appropriate permissions must be given to allow clients to upload to this directory by means of IIS using the BITS ISAPI component. This directory must be created at install time; it is not automatically created by the service.

`IncomingPayloadVirtualDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

IIS virtual directory mapped to **IncomingPayloadDir**.

`OutgoingPayloadDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory that is used to hold message payloads that will be downloaded by clients.

`OutgoingPayloadVirtualDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

IIS virtual directory mapped to **OutgoingPayloadDir**.

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

## Remarks

An instance of this class should exist only if IIS has been configured to work with CCMEXEC, that is, IIS must be installed and the appropriate physical and virtual directories must be set up correctly. If this instance is omitted, CCMEXEC operates without using IIS, thus losing some functionality.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).