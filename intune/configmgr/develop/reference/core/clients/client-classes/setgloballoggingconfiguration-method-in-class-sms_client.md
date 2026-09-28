---
layout: Conceptual
title: SetGlobalLoggingConfiguration Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client
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
description: Learn how to define the global logging configuration for the client with SetGlobalLoggingConfiguration method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 429a2a64-4597-0b31-52ee-518fdeeff7f5
document_version_independent_id: fdb72ecc-2701-6e79-fa16-149a121a2439
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client.md
cmProducts: []
platformId: 03428b1d-47be-690e-a735-65f3c0677f35
---

# SetGlobalLoggingConfiguration Method - Configuration Manager | Microsoft Learn

The `SetGlobalLoggingConfiguration` method, in Configuration Manager, defines the global logging configuration for the client. This configuration represents either component-level logging or default logging if component-level logging isn't defined.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 SetGlobalLoggingConfiguration(
     UInt32 LogLevel,
     UInt32 LogMaxSize,
     UInt32 LogMaxHistory,
     Boolean DebugLogging
);
```

#### Parameters

`LogLevel` Data type: `UInt32`

Qualifiers: [in]

The level of detail that the log will capture. Possible values are shown below. The default value is 1.

| Value | Description |
| --- | --- |
| 0 | Verbose logging |
| 1 | Normal logging |
| 2 | No logging |

`LogMaxSize` Data type: `UInt32`

Qualifiers: [in]

The maximum size, in bytes, of a given log file.

`LogMaxHistory` Data type: `UInt32`

Qualifiers: [in]

The number of incremented log files to accumulate before deleting. When this number has been reached, the creation of a new log file results in the deletion of the oldest existing log file.

`DebugLogging` Data type: `Boolean`

Qualifiers: [in]

`true` if debug logging should be enabled. Debug logging is rarely used except for troubleshooting.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Remarks

This method manipulates registry keys. These keys shouldn't be manipulated directly. However, for reference, these keys can be found at HKEY\_LOCAL\_MACHINE/Software/Microsoft/CCM/logging/@GLOBAL. Enabling debug logging with `DebugLogging` results in the creation of a new key: HKEY\_LOCAL\_MACHINE/Software/Microsoft/CCM/logging/debuglogging.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).