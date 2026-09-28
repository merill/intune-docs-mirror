---
layout: Conceptual
title: SMS_Windows8Application Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8application-client-wmi-class
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
description: Learn how to define a Windows 8 style application or a Windows Store application in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1f877a82-0cc9-c935-1f19-27ec41012e9b
document_version_independent_id: 45a063db-a22e-6661-208b-4f07a213d619
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8application-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_windows8application-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8application-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 633d092f-9b76-7083-ce3e-946a314167d7
---

# SMS_Windows8Application Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `SMS_Windows8Application` class is a client Windows Management Instrumentation (WMI) class that defines a Windows 8 style application or a Windows Store application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Windows8Application
{
      String ApplicationName;
      String Architecture;
      String DependencyApplicationNames;
      String FamilyName;
      String FullName;
      String InstalledLocation;
      Boolean IsFramework;
      Boolean ConfigMgrManaged;
      String Publisher;
      String PublisherId;
      String Version;
};
```

## Methods

The `SMS_Windows8Application` class does not define any methods.

## Properties

`ApplicationName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the application.

`Architecture` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Specifies the processor architecture supported by an application. Possible values are:

| Value | Description |
| --- | --- |
| X86 or x86 | The x86 processor architecture. |
| Arm or arm | The ARM processor architecture. |
| X64 or x64 | The x64 processor architecture. |
| Neutral or neutral | A neutral processor architecture. |
| Unknown or unknown | An unknown processor architecture. |

`DependencyApplicationNames` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Dependency application names.

`FamilyName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Family name.

`FullName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Full name.

`InstalledLocation` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Installation location.

`IsFramework` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if another application can declare a dependency on this application.

`ConfigMgrManaged` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the application is managed by Configuration Manager.

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Application publisher.

`PublisherId` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Application publisher identifier.

`Version` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Application version.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).