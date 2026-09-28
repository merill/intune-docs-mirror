---
layout: Conceptual
title: SMS_G_System_EndpointProtectionStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_g_system_endpointprotectionstatus-server-wmi-class
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
description: Learn how to use the SMS_G_System_EndpointProtectionStatus class to represent the status of Endpoint Protection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 660a78ce-6b51-8431-ae80-4f1690fa9e2c
document_version_independent_id: eea11607-9996-10cd-fc12-afdc46178dd6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_g_system_endpointprotectionstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_g_system_endpointprotectionstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_g_system_endpointprotectionstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9418731-38ba-00ea-f95a-7d66441dee35
---

# SMS_G_System_EndpointProtectionStatus Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_EndpointProtectionStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents status of Endpoint Protection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_EndpointProtectionStatus : SMS_G_System
{
    Boolean AmFullscanRequired;
    Boolean AmManualStepsRequired;
    Boolean AmOfflineScanRequired;
    Boolean AmRecentlyCleaned;
    Boolean AmRemediationFailed;
    Boolean AmRestartRequired;
    Boolean AmThreatActivity;
    Boolean AtRisk;
    Boolean EnforcementFailed;
    Boolean EnforcementSucceeded;
    Boolean Inactive;
    Boolean InstallFailed;
    Boolean NoSignature;
    Boolean NotClient;
    Boolean NotYetInstalled;
    Boolean PendingReboot;
    Boolean Protected;
    UInt32 ResourceID;
    Boolean SignatureOlderThan7Days;
    Boolean SignatureUpTo1DayOld;
    Boolean SignatureUpTo3DaysOld;
    Boolean SignatureUpTo7DaysOld;
    Boolean Unhealthy;
    Boolean Unsupported;
};
```

## Methods

The `SMS_G_System_EndpointProtectionStatus` class does not define any methods.

## Properties

`AmFullscanRequired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is pending a full scan due to threat action.

`AmManualStepsRequired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is pending manual steps due to threat action.

`AmOfflineScanRequired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is pending an offline scan due to threat action.

`AmRecentlyCleaned` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if a threat was detected and cleaned recently.

`AmRemediationFailed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client failed to remediate the threat.

`AmRestartRequired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is pending a reboot due to threat action.

`AmThreatActivity` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if a threat was detected.

`AtRisk` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client has the policy to enable EndPoint Protection, however, the SCEP agent is not successfully installed (or pending a reboot to finish the installation), no signature is installed, the signature is too old, the client is inactive (from client status perspective) or the client failed to apply antimalware policy and so on.

`EnforcementFailed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client failed to apply policy.

`EnforcementSucceeded` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client successfully applied policy.

`Inactive` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is inactive.

`InstallFailed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client failed to install the Endpoint Protection client.

`NoSignature` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if no signature is installed on this client.

`NotClient` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is not a Configuration Manager client.

`NotYetInstalled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the Endpoint Protection client is not installed.

`PendingReboot` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is pending a restart to complete the Endpoint Protection installation.

`Protected` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is well protected.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Client resource identifier.

`SignatureOlderThan7Days` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the signature is older than 7 days.

`SignatureUpTo1DayOld` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the signature is up to 1 day old.

`SignatureUpTo3DaysOld` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the signature is up from 1 to 3 days old.

`SignatureUpTo7DaysOld` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the signature is up from 3 to 7 days old.

`Unhealthy` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the client is unhealthy from a client status perspective.

`Unsupported` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the Endpoint Protection client is not supported on this client platform.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).