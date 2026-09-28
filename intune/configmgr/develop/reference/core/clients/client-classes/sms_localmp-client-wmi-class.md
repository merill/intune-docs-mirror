---
layout: Conceptual
title: SMS_LocalMP Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_localmp-client-wmi-class
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
description: The SMS_LocalMP class is a client Windows Management Instrumentation class, in Configuration Manager, that represents the local management point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 55447209-889d-08e9-a0f4-38ed6c87cefd
document_version_independent_id: c8370eaa-2e45-8c67-19fc-b04e6ada81b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_localmp-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_localmp-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_localmp-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c705e5bb-1e42-006b-a18a-7327b6ae3b1c
---

# SMS_LocalMP Class - Configuration Manager | Microsoft Learn

The `SMS_LocalMP` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents the local management point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_LocalMP
{
      String Capabilities;
      UInt32 Index;
      String MasterSiteCode;
      String Name;
      String Protocol;
      String SiteCode;
      UInt32 Version;
};
```

## Methods

The `SMS_LocalMP` class does not define any methods.

## Properties

`Capabilities` Data type: `String`

Access type: Read/Write

Qualifiers: None

Capabilities of the local management point.

`Index` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For local Management Point rotation.

`MasterSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

The master site code for the local management point.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the local management point.

`Protocol` Data type: `String`

Access type: Read/Write

Qualifiers: None

The network protocol used for the local management point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code for the site supporting the local management point.

`Version` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The version of the local management point.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).