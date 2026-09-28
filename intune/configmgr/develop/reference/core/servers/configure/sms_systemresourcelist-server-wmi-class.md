---
layout: Conceptual
title: SMS_SystemResourceList Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class
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
description: Learn how to map network abstraction layer (NAL) paths, resource types, site codes, and role names for system resources located on site servers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4cd8da9e-990c-1a5d-0419-a64b972dfaf3
document_version_independent_id: 3e172a83-c731-51ac-2d1e-a6df0b837145
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a8969278-c845-0a85-77c4-e59044e192f0
---

# SMS_SystemResourceList Class - Configuration Manager | Microsoft Learn

The `SMS_SystemResourceList` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps network abstraction layer (NAL) paths, resource types, site codes, and role names for system resources located on site servers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SystemResourceList : SMS_BaseClass
{
     Boolean InternetEnabled;
     Boolean InternetShared;
     String NALPath;
     String ResourceType;
     String RoleName;
     String ServerName,
     String ServerRemoteName,
     String SiteCode,
     UInt32 SslState
};
```

## Methods

The `SMS_SystemResourceList` class doesn't define any methods.

## Properties

`InternetEnabled` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if this role system resource is Internet enabled. The default value is `false`.

`InternetShared` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the site system resource instance can serve both internet clients and intranet clients. It has meaning only if the `InternetEnabled` property is also set to `true`.

`NALPath` Data type: `String`

Access type: Read Only

Qualifiers: [key]

NAL path of the system resource. The default value is "".

`ResourceType` Data type: `String`

Access type: Read Only

Qualifiers: [key]

Type of the system resource, such as a Windows NT Server. The default value is "".

`RoleName` Data type: `String`

Access type: Read Only

Qualifiers: [key]

Role of the server. The default value is "".

`ServerName` Data type: `String`

Access type: Read Only

Qualifiers: None

Name of the server. The default value is "".

`ServerRemoteName` Data type: `String`

Access type: Read Only

Qualifiers: None

Fully qualified domain name (FQDN) for the site system on the intranet. The default value is "".

`SiteCode` Data type: `String`

Access type: Read Only

Qualifiers: [key, SizeLimit("3")]

Site that owns the system resource. The default value is "".

`SslState` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

SSL state description. Possible values are:

| Value | SSL state |
| --- | --- |
| 0 | HTTP |
| 1 | HTTPS |
| 2 | Not applicable. The property is only applicable for a site system role that is client facing. |
| 3 | Always HTTPS |
| 4 | Always HTTP |

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).