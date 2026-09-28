---
layout: Conceptual
title: CCM_Service_BITSConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class
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
description: Learn how to use CCM_ServiceBITSConfiguration class which supports BITS-related settings used by CCMEXEC for uploading and downloading message payloads.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2cea100e-e354-2821-24e6-794cdfb3f944
document_version_independent_id: fd686452-1ce0-e96b-b2ed-76ea3b8497be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c260231-4472-1af0-7daf-7a0a16198097
---

# CCM_Service_BITSConfiguration Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Service_BITSConfiguration` class is a client Windows Management Instrumentation (WMI) class that supports Background Intelligent Transfer Service (BITS)-related settings used by CCMEXEC for uploading and downloading message payloads. The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_BITSConfiguration : CCM_Policy
{
      UInt8 DummyKey;
      UInt32 MinimumRetryDelay;
      UInt32 NoProgressTimeout;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Service_BITSConfiguration` class does not define any methods.

## Properties

`DummyKey` Data type: `UInt8`

Access type: Read/Write

Qualifiers: None

This value is used as the WMI key for a singleton policy and has no other effect.

`MinimumRetryDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Retry delay to pass to BITS when uploading or downloading message payloads (in minutes). If the value is 0 or `null`, BITS defaults are used.

`NoProgressTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

No-progress timeout to pass to BITS when uploading or downloading message payloads (in minutes). If the value is `null` or 0, BITS defaults are used.

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

Qualifiers: Key

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