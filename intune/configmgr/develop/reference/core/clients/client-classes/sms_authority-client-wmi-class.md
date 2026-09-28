---
layout: Conceptual
title: SMS_Authority Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_authority-client-wmi-class
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
description: In Configuration Manager, the SMS_Authority class is a client Windows Management Instrumentation class that represents the Configuration Manager site that manages the client.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: be292bf2-97ab-481e-cc40-e0d809d17dcb
document_version_independent_id: 2e2605c1-1e8b-cb3c-604d-d4e6a1d34eb1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_authority-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_authority-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_authority-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f17f22ca-e283-2678-d9e9-4b53798e94bc
---

# SMS_Authority Class - Configuration Manager | Microsoft Learn

The `SMS_Authority` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents the Configuration Manager site that manages the client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Authority : CCM_Authority
{
      String Capabilities;
      String CurrentManagementPoint;
      UInt32 Index;
      String Name;
      UInt32 PolicyOrder;
      String PolicyRequestTarget;
      String Protocol;
      String SigningCertificate;
      UInt32 Version;
};
```

## Methods

The `SMS_Authority` class does not define any methods.

## Properties

`Capabilities` Data type: `String`

Access type: Read/Write

Qualifiers: None

Reserved.

`CurrentManagementPoint` Data type: `String`

Access type: Read/Write

Qualifiers: None

The current management point for the site.

`Index` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For assigned Management Point rotation.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the authority.

`PolicyOrder` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Determines the priority of the authority when resolving policy conflicts. The lower the order, the higher the priority of the authority's policy.

`PolicyRequestTarget` Data type: `String`

Access type: Read/Write

Qualifiers: None

Specifies the target for requesting policy assignments. If this value is NULL, no policy is requested for this authority.

`Protocol` Data type: `String`

Access type: Read/Write

Qualifiers: None

Reserved.

`SigningCertificate` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site signing certificate. This is only relevant in native mode.

`Version` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The version of the authority.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).