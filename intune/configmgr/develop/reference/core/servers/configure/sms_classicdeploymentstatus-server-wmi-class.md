---
layout: Conceptual
title: SMS_ClassicDeploymentStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_classicdeploymentstatus-server-wmi-class
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
description: The SMS_ClassicDeploymentStatus WMI class is an SMS Provider server class that represents classic software distribution deployment status.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 507e3ab1-9dee-3619-18b9-da7d43f66af6
document_version_independent_id: 8c167254-e569-8614-61f6-833053c8b8f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_classicdeploymentstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_classicdeploymentstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_classicdeploymentstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 580c9302-e812-981f-3a2d-439cb0c8fb32
---

# SMS_ClassicDeploymentStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ClassicDeploymentStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents classic software distribution deployment status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClassicDeploymentStatus : SMS_BaseClass
{
    UInt32 Assets;
    String CollectionID;
    String CollectionName;
    String DeploymentID;
    DateTime DeploymentTime;
    Boolean IsDeviceDeployment;
    String MessageDescription;
    UInt32 MessageID;
    String PackageID;
    String PackageName;
    String ProgramName;
    UInt32 Purpose;
    UInt32 StatusType;
    DateTime SummarizationTime;
};
```

## Methods

The `SMS_ClassicDeploymentStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Number of assets related to the status.

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Existing collection to which the advertisement is targeted.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the collection to which the advertisement is advertising.

`DeploymentID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

A unique auto-generated key.

`DeploymentTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The time of the deployment.

`IsDeviceDeployment` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the deployment is for mobile devices.

`MessageDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Message description.

`MessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Software distribution or software update message ID.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

ID for an existing package associated with the advertisement.

`PackageName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the advertised package.

`ProgramName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The program name of the program related to the package that the advertisement will advertise.

`Purpose` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Purpose.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Status Type.

| Value | Status type |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |
| 5 | Error |

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

The last time the summarization task was run for this application or current time in UTC if it is missing.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).