---
layout: Conceptual
title: UpdateAutoUpgradeConfigs Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/updateautoupgradeconfigs-method-in-class-sms_site
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
description: The UpdateAutoUpgradeConfigs Windows Management Instrumentation class method, in Configuration Manager, updates configurations for autoupgrade settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 398cab40-bebd-3bb7-9a9b-3a9a9a7b257d
document_version_independent_id: e6168384-b509-4a54-98f9-6c76579614ef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/updateautoupgradeconfigs-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/updateautoupgradeconfigs-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/updateautoupgradeconfigs-method-in-class-sms_site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c7ad1e2-6c42-e042-4e50-2a67b15906a5
---

# UpdateAutoUpgradeConfigs Method - Configuration Manager | Microsoft Learn

The `UpdateAutoUpgradeConfigs` Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates configurations for autoupgrade settings.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 UpdateAutoUpgradeConfigs(
     String ClientVersion,
     Boolean IsProgramEnabled,
     UInt32 AdvertisementDuration,
     UInt32 ValidationInterval,
     UInt32 ValidationFailureInterval,
     Boolean AllowPrestage,
     Boolean AllowFallbackToContentSource,
     UInt32 DownloadOptionsInSlowNetwork,
     Boolean ExcludeServers,
     Boolean OverrideServiceWindow,
     Boolean IgnoreNonPersistableVM
);
```

#### Parameters

`ClientVersion` Data type: `String`

Qualifiers: [in]

The version of the client.

`IsProgramEnabled` Data type: `Boolean`

Qualifiers: [in]

`true` if the program is enabled.

`AdvertisementDuration` Data type: `UInt32`

Qualifiers: [in]

Advertisement duration in days.

`ValidationInterval` Data type: `UInt32`

Qualifiers: [in]

Validation interval in hours, if the previous validation is successful.

`ValidationFailureInterval` Data type: `UInt32`

Qualifiers: [in]

Validation interval in hours, if the previous validation is failed.

`AllowPrestage` Data type: `Boolean`

Qualifiers: [in]

`true` if autoupgrade package distributed to pre-stage distribution point is allowed.

`AllowFallbackToContentSource` Data type: `Boolean`

Qualifiers: [in]

`true` if fallback to content source is allowed.

`DownloadOptionInSlowNetwork` Data type: `UInt32`

Qualifiers: [in]

Download options in slow network. Possible values are:

| Value | Download option |
| --- | --- |
| 0 | Do not download. |
| 1 | Download from distribution point and run locally. |
| 2 | Run from distribution point. |

`ExcludeServers` Data type: `Boolean`

Qualifiers: [in]

Indicates whether autoupgrade should be skipped on servers.

`OverrideServiceWindow` Data type: `Boolean`

Qualifiers: [in]

Indicates whether the upgrade on the client occurs in service window.

`IgnoreNonPersistableVM` Data type: `Boolean`

Qualifiers: [in]

Indicates whether autoupgrade should be skipped on non-persistent virtual machines.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).