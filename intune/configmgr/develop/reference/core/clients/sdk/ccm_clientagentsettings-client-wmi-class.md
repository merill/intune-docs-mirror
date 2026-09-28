---
layout: Conceptual
title: CCM_ClientAgentSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_clientagentsettings-client-wmi-class
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
description: A client class, in Configuration Manager, that contains common client agent settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f86adf98-b349-743f-feaa-ad115e18b26c
document_version_independent_id: e4a92b07-c78c-a001-cd80-454748bf76c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_clientagentsettings-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_clientagentsettings-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_clientagentsettings-client-wmi-class.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/81a11282-2f1c-4a63-95c5-6e6f262fea55
platformId: f9db5f44-873a-dc73-dd84-e30917b40c29
---

# CCM_ClientAgentSettings Class - Configuration Manager | Microsoft Learn

The `CCM_ClientAgentSettings` WMI class is a client class, in Configuration Manager, that contains common client agent settings.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_ClientAgentSettings
{
     String BrandingTitle;
     UInt32 DayReminderInterval;
     Boolean DisplayNewProgramNotification;
     UInt32 EnableThirdPartyOrchestration;
     UInt32 HourReminderInterval;
     UInt32 InstallRestriction;
     UInt32 ReminderInterval;
     UInt32 SuspendBitLocker;
     UInt32 SystemRestartTurnaroundTime;
};
```

## Methods

The `CCM_ClientAgentSettings` class does not define any methods.

## Properties

`BrandingTitle` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Title of the brand displayed in Configuration Manager. It maps to the client agent setting in Computer Agent, called **Organization name displayed in Software Center**

`DayReminderInterval` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Interval at which notifications are displayed to the user when there is required software pending and the earliest required deadline is less than 24 hours and greater than 1 hour.

`DisplayNewProgramNotification` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`false`, if no notifications are shown to the user for software availability or software installations. Only restart notifications are displayed. This property is mapped to the **Suppress notifications for new deployments** client agent setting in the Configuration Manager Admin Console.

`EnableThirdPartyOrchestration` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Flag to indicate whether Software Updates and Software Distribution agents wait for third-party components to install updates and applications.

`HourReminderInterval` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Interval at which notifications are displayed to the user when there is required software pending and the earliest required deadline is less than 1 hour.

`InstallRestriction` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Restriction flag to indicate who can initiate the installation. These options can be selected from the UI. The following table shows the list of possible values.

| Value | Permission |
| --- | --- |
| 0 | Everyone |
| 1 | Local administrators only |
| 2 | Not used |
| 3 | Local administrators and primary users |
| 4 | No one |

`ReminderInterval` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Interval at which notifications are displayed to the user when there is required software pending and the earliest required deadline is greater than 24 hours.

`SuspendBitLocker` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Flag to indicate whether to suspend BitLocker Drive Protection PIN protectors for the restart initiated by Configuration Manager.

`SystemRestartTurnaroundTime` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Estimated turnaround time, in seconds, for a system restart.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).