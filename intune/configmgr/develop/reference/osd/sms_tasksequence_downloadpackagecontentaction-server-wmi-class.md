---
layout: Conceptual
title: SMS_TaskSequence_DownloadPackageContentAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_downloadpackagecontentaction-server-wmi-class
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
description: Represents a task sequence action that downloads the contents of a package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9aa0f142-8564-8114-1188-aaeec91ad7dc
document_version_independent_id: 58dd2041-087d-8e6d-839f-c004db1f49a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_downloadpackagecontentaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_downloadpackagecontentaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_downloadpackagecontentaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 117f1d5b-4ca0-56cc-0d43-c3e5e6fef3ac
---

# SMS_TaskSequence_DownloadPackageContentAction Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_DownloadPackageContentAction` Windows Management Instrumentation (WMI) class is an SMS provider server class, in Configuration Manager, that represents a task sequence action that downloads the contents of a package.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_DownloadPackageContentAction : SMS_TaskSequence_Action
{
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueDownloadOnError;
    Boolean ContinueOnError;
    String Description;
    String DestinationCustomPath;
    String DestinationLocationType;
    String DestinationVariable;
    String DownloadPackages;
    Boolean Enabled;
    String Name;
    UInt32 NumPackages;
    SMS_TaskSequence_PackageInfo PackageInfo[];
    String SupportedEnvironment;
    UInt32 Timeout;
};

```

## Methods

The `SMS_TaskSequence_DownloadPackageContentAction` class does not define any methods.

## Properties

`Condition` Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`ContinueDownloadOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to continue to the next package if a package fails to download. The default value is `true`.

`ContinueOnError` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`DestinationCustomPath` Data type: `String`

Access type: Read/Write

Qualifiers: [VariableName("OSDDownloadDestinationPath")]

The destination path.

`DestinationLocationType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, ValueMap]

The destination location type. The default value is TSCache. Possible values are:

| Value |
| --- |
| TSCache |
| CCMCache |
| Custom |

`DestinationVariable` Data type: `String`

Access type: Read/Write

Qualifiers: none

The destination variable.

`DownloadPackages` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null, TaskSequencePackageList]

Comma separated list of package Ids to be downloaded.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("1-100")]

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`NumPackages` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [VariableName("OSDPackageCount")]

The total number of packages.

`PackageInfo` Data type: `SMS_TaskSequence_PackageInfo Array`

Access type: Read/Write

Qualifiers: [VariableName("OSDPackage")]

An array of task sequence information package information.

`SupportedEnvironment` Data type: `String`

Access type: Read/Write

Qualifiers: none

The default value is WinPEandFullOS. See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_TaskSequence_Action Server WMI Class](sms_tasksequence_action-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).