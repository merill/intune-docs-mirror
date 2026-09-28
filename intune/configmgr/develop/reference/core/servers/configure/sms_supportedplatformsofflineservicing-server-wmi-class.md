---
layout: Conceptual
title: SMS_SupportedPlatformsOfflineServicing Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class
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
description: In Configuration Manager, the SMS_SupportedPlatformsOfflineServicing Windows Management Instrumentation class is an SMS Provider server class that used to determine which operating system images can be serviced offline.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3080e913-3687-1387-0f72-d30b2a53bcdd
document_version_independent_id: 68ee0551-2f8c-d78e-387b-0678e1836bae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a133eb8c-5c26-c567-874e-5b57ea96856c
---

# SMS_SupportedPlatformsOfflineServicing Class - Configuration Manager | Microsoft Learn

The `SMS_SupportedPlatformsOfflineServicing` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that used to determine which operating system images can be serviced offline.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SupportedPlatformsOfflineServicing : SMS_BaseClass
{
    String Name;
    String OsVersionBuild;
    String ProductType;
};
```

## Methods

The `SMS_SupportedPlatformsOfflineServicing` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

The name of the operating system that supports offline servicing, such as "Windows 8" or "Windows 8 Server".

`OsVersionBuild` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

The version and build number of Windows that supports offline servicing, such as 6.0.6001.

`ProductType` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

Product type. Two string values are used: "WinNT" - to indicate a client operating system type, "ServerNT" - to indicate server operating system type. Possible values are:

| String Value | Operating System Type |
| --- | --- |
| ServerNT | Server |
| WinNT | Client |

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).