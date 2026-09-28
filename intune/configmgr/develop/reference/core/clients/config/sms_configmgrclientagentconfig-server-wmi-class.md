---
layout: Conceptual
title: SMS_ConfigMgrClientAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_configmgrclientagentconfig-server-wmi-class
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
description: Learn how to specify the general settings for communication between server and client using SMS_COnfigMgrClientAgentConfig.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9e2a40bf-f0f5-5ba2-dd26-289f83416112
document_version_independent_id: f82a54d9-1f17-5c6a-033a-c1cb15927de0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_configmgrclientagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_configmgrclientagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_configmgrclientagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e7ed706-f5d7-4411-be22-6fcf98d10e44
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b4084e3b-5e61-4e73-886a-780c8f7b0fa1
platformId: 48e67069-496f-ff97-e6e6-cf19d810feb8
---

# SMS_ConfigMgrClientAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigMgrClientAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies the general settings for communication between server and client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigMgrClientAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    Boolean AddPortalToTrustedSiteList;
    Boolean AllowPortalToHaveElevatedTrust;
    UInt32 AgentID;
    String BrandingTitle;
    UInt32 DayReminderInterval;
    Boolean DisplayNewProgramNotification;
    Boolean EnableHealthAttestation;
    UInt32 EnableThirdPartyOrchestration;
    UInt32 GracePeriodHours;
    UInt32 HourReminderInterval;
    UInt32 InstallRestriction;
    String OnPremHAServiceUrl;
    String OSDBrandingSubTitle;
    String PortalUrl;
    UInt32 PowerShellExecutionPolicy;
    UInt32 ReminderInterval;
    String SUMBrandingSubTitle;
    UInt32 SuspendBitLocker;
    String SWDBrandingSubTitle;
    UInt32 SystemRestartTurnaroundTime;
    Boolean UseNewSoftwareCenter;
    Boolean UseOnPremHAService;
};
```

## Methods

The `SMS_ConfigMgrClientAgentConfig` class does not define any methods.

## Properties

`AddPortalToTrustedSiteList` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Add default Application Catalog website to the Internet Explorer trusted sites zone.

`AllowPortalToHaveElevatedTrust` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Allow Silverlight applications to run in elevated trust mode.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Configuration Manager Client Agent ID is 4.

`BrandingTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

Organization name displayed in Software Center.

`DayReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Deployment deadline greater than 24 hours, remind user every (hours).

`DisplayNewProgramNotification` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if notifications are shown to a user when a new program is made available.

`EnableHealthAttestation` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether [Windows 10 Device Health Attestation](/en-us/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices) is enabled.

`EnableThirdPartyOrchestration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Enable third party orchestration.

`GracePeriodHours` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of hours in the enforcement grace period.

Define an enforcement grace period to give users more time to install required application deployments or software updates beyond any deadlines you configured.

`HourReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Deployment deadline less than 24 hours, remind user every (hours).

`InstallRestriction` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Install permissions.

| Possible values |
| --- |
| All users |
| Only administrators |
| Only administrators and primary users |
| No users |

`OnPremHAServiceUrl` Data type: `String`

Access type: Read/Write

Qualifiers: none

The URL for the on-premises Health Attestation Service.

`OSDBrandingSubTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

The operating system deployment branding subtitle.

`PortalUrl` Data type: `String`

Access type: Read/Write

Qualifiers: none

Default Application Catalog website point.

`PowerShellExecutionPolicy` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

PowerShell execution policy.

| Value | Definition |
| --- | --- |
| 0 | Bypass |
| 1 | Restricted |

`ReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Deployment deadline less than 1 hour, remind user every (minutes).

`SUMBrandingSubTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

The software updates branding subtitle.

`SuspendBitLocker` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

`true` to disable PIN protector on the system volume if the reboot is initiated by CcmExec (not including the user explicitly rebooting from the reboot UI). After the reboot, the PIN protector is enabled. This enables a computer reboot without user intervention.

| Value | Definition |
| --- | --- |
| 0 | Never disable PIN protection. |
| 1 | Always disable PIN protection. |

`SWDBrandingSubTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

The software distribution branding subtitle.

`SystemRestartTurnaroundTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The estimated turnaround time for system reboot, in seconds.

`UseNewSoftwareCenter` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether the updated Software Center is used.

`UseOnPremHAService` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether the on-premises Health Attestation Service is used.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).