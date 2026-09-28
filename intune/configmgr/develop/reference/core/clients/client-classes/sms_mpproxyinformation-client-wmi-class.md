---
layout: Conceptual
title: SMS_MPProxyInformation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_mpproxyinformation-client-wmi-class
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
description: A client Windows Management Instrumentation class that represents information about a proxy management point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 666a3e42-13ca-7f49-0cb5-f8d87047db56
document_version_independent_id: 1073b828-b277-b325-d8c2-ae46bf880a7f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_mpproxyinformation-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_mpproxyinformation-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_mpproxyinformation-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8fa37185-2539-ddc3-5b46-f3b1b56099db
---

# SMS_MPProxyInformation Class - Configuration Manager | Microsoft Learn

The `SMS_MPProxyInformation` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents information about a proxy management point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MPProxyInformation
{
      String Capabilities;
      UInt32 Index;
      String Name;
      String Protocol;
      String SiteCode;
      String State;
      UInt32 Version;
};
```

## Methods

The `SMS_MPProxyInformation` class does not define any methods.

## Properties

`Capabilities` Data type: `String`

Access type: Read/Write

Qualifiers: None

Capabilities of the proxy management point.

`Index` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For proxy Management Point rotation.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the proxy management point.

`Protocol` Data type: `String`

Access type: Read/Write

Qualifiers: None

The network protocol used by the proxy management point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code of the site for the proxy management point.

`State` Data type: `String`

Access type: Read/Write

Qualifiers: None

The state of the proxy management point.

`Version` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The version of the proxy management point.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).