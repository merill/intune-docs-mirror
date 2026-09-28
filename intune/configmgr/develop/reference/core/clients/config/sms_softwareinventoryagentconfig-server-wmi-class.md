---
layout: Conceptual
title: SMS_SoftwareInventoryAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_softwareinventoryagentconfig-server-wmi-class
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
description: Learn how to specify how client computers retrieve software inventory in Configuration Manager using SMS_SoftwareInventoryAgentConfig.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5820c0f4-7b67-71c2-98d5-92583059cc00
document_version_independent_id: f4b613af-b89c-f5da-e681-2ef572f8a8a1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_softwareinventoryagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_softwareinventoryagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_softwareinventoryagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f2c3442f-16c7-dbcc-d9df-870fc80b5d6b
---

# SMS_SoftwareInventoryAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareInventoryAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers retrieve software inventory.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareInventoryAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    String CollectableFileExclude[];
    String CollectableFileMaxSize[];
    String CollectableFilePaths[];
    String CollectableFiles[];
    String CollectableFileSubdirectories[];
    Boolean Enabled;
    String Exclude[];
    String ExcludeWindirAndSubfolders[];
    String InventoriableTypes[];
    String Path[];
    UInt32 QueryTimeout;
    UInt32 ReportOptions;
    UInt32 ReportTimeout;
    UInt32 ScanInterval;
    String Schedule;
    String Subdirectories[];
};
```

## Methods

The `SMS_SoftwareInventoryAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Software Updates Agent ID is 2.

`CollectableFileExclude` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

`true` if encrypted and compressed files are excluded in the file collection settings. The value in the array should be `true` or `false`.

`CollectableFileMaxSize` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

Maximum size for all collected files (KB).

`CollectableFilePaths` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The list of file paths to collect.

`CollectableFiles` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The list of files to collect.

`CollectableFileSubdirectories` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

`true` if files in subfolders are collected in the file collection settings. The value in the array should be `true` or `false`.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`Exclude` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

`true` if encrypted and compressed files are excluded in the file inventory settings. The value in the array should be `true` or `false`.

`ExcludeWindirAndSubfolders` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

`true` if files in the Windows folder are excluded in the file inventory settings. The value in the array should be `true` or `false`.

`InventoriableTypes` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The list of file types to inventory.

`Path` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The list of file path to be inventoried in the file inventory settings.

`QueryTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The maximum time, in seconds, for querying file information on the client. The default value is 1 week.

`ReportOptions` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The reporting details. Possible values are:

| Value | Report options |
| --- | --- |
| 1 | Product Only |
| 2 | File Only |
| 7 | Full Details |

`ReportTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum time, in seconds, that the client messaging framework attempts to transmit the report, if the destination endpoint is unreachable. The default value is 1 week.

`ScanInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Delay, in milliseconds, to pass to the software inventory provider for the software scan.

`Schedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Software inventory and file collection schedule.

`Subdirectories` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

`true` if files in subfolders are inventoried in the file inventory settings. The value in the array should be `true` or `false`.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).