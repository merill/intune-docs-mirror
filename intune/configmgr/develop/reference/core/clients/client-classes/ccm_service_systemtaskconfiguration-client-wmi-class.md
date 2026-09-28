---
layout: Conceptual
title: CCM_Service_SystemTaskConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_systemtaskconfiguration-client-wmi-class
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
description: In Configuration Manager, the CCM_Service_SystemTaskConfiguration class is a client WMI class that supports system task configuration for the CCMEXEC service.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: eb540682-f7d3-6b5f-b8ca-3801d43b02e8
document_version_independent_id: 296da7ba-525c-4321-87f2-3963649efd47
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_systemtaskconfiguration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_service_systemtaskconfiguration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_systemtaskconfiguration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 67dcb18f-594f-2013-9c4f-37aa29a3a2cd
---

# CCM_Service_SystemTaskConfiguration Class - Configuration Manager | Microsoft Learn

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Service_SystemTaskConfiguration` class is a client Windows Management Instrumentation (WMI) class that supports system task configuration for the CCMEXEC service.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_SystemTaskConfiguration : CCM_Policy
{
      String CoClass;
      String DisplayName;
      String Event;
      String Name;
      UInt32 Order;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String ThreadType;
};
```

## Methods

The `CCM_Service_SystemTaskConfiguration` class does not define any methods.

## Properties

`CoClass` Data type: `String`

Access type: Read/Write

Qualifiers: None

Class ID or program ID of the COM class that implements the system task.

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Display name of the system task.

`Event` Data type: `String`

Access type: Read/Write

Qualifiers: None

Event on which the system task should be invoked.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [Realkey]

Name of the system task, which must be unique on the computer.

`Order` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Order value of the task. Tasks with lower order values run before tasks with higher values. Tasks with the same order value run simultaneously (no ordering between them is guaranteed).This value defaults to 0 if a value is not specified.

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

`ThreadType` Data type: `String`

Access type: Read/Write

Qualifiers: None

Thread type on which the endpoint should be invoked.

## Remarks

There is an instance of this class for each system task on the computer.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).