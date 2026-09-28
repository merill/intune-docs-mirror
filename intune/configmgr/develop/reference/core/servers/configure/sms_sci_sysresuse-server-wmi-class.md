---
layout: Conceptual
title: SMS_SCI_SysResUse Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class
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
description: An SMS Provider server class that represents a specific usage of a server or other network resource.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7ab9e4fd-1b32-e777-9a52-3c761fc3bd86
document_version_independent_id: 725ab67f-a548-3931-d007-daa3759d32f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 639bc0c9-4dab-ea72-157e-b83fcb83b6a3
---

# SMS_SCI_SysResUse Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_SysResUse` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a specific usage of a server or other network resource.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_SysResUse : SMS_SiteControlItem
{
    UInt32 FileType;
    String ItemName;
    String ItemType;
    String NALPath;
    String NALType;
    String NetworkOSPath;
    SMS_EmbeddedPropertyList PropLists[];
    SMS_EmbeddedProperty Props[];
    UInt32 RoleCount;
    String RoleName;
    SMS_ServiceWindow ServiceWindows[];
    String SiteCode;
    UInt32 SslState;
    UInt32 Type;
};
```

## Methods

The `SMS_SCI_SysResUse` class doesn't define any methods.

## Properties

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration, key, enumeration, key]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`NALPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

Path to the NAL resource. The default value is "".

`NALType` Data type: `String`

Access type: Read/Write

Qualifiers: none

Friendly name for the `NetworkOSPath` value. For example, "Windows NT Server". The default value is "".

`NetworkOSPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

The network operating system path. The default value is "".

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: none

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the network resource.

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: none

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the network resource.

`RoleCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of roles.

`RoleName` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("64"), stringenumeration]

Role of the server. The default value is "".

`ServiceWindows` Data type: `SMS_ServiceWindow` Array

Access type: Read-only

Qualifiers: [read, lazy]

List of service windows.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, key, sizelimit]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`SslState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

SSL state description. Possible values are:

| Value | SSL state |
| --- | --- |
| 0 | HTTP |
| 1 | HTTPS |
| 2 | Not applicable. The property is only applicable for a site system role that is client facing. |
| 3 | Always HTTPS |
| 4 | Always HTTP |

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Returns the site server type if the site system role is colocated on the site server. Possible values are:

| Value | Site server type |
| --- | --- |
| 1 | The site system role is colocated on the secondary site server. |
| 2 | The site system role is colocated on the primary site server. |
| 4 | The site system role is colocated on the CAS site server. |
| 8 | The site system role isn't colocated with any site server. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).