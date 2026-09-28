---
layout: Conceptual
title: SMS_G_System_AdvancedThreatProtectionHealthStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_advancedthreatprotectionhealthstatus-server-wmi-class
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
ms.date: 2019-05-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: An overview of SMS_G_System_AdvancedThreatProtectionHealthStatus Server WMI Class
locale: en-us
document_id: 30215eba-0531-2d42-cce7-7b5036b414d7
document_version_independent_id: 098edc0d-e3b7-9ac0-b87a-90e1d66965c0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_advancedthreatprotectionhealthstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_advancedthreatprotectionhealthstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_advancedthreatprotectionhealthstatus-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 33fe2838-779a-eba3-5e22-dfe5a91bec73
---

# SMS_G_System_AdvancedThreatProtectionHealthStatus Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_AdvancedThreatProtectionHealthStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Defender for Endpoint client health status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_AdvancedThreatProtectionHealthStatus : SMS_G_System
{
    DateTime LastConnected;
    UInt32 OnboardingState;
    String OrgId;
    UInt32 ResourceID;
    Boolean SenseIsRunning;
};
```

## Methods

The `SMS_G_System_AdvancedThreatProtectionHealthStatus` class does not define any methods.

## Properties

`LastConnected` Data type: `DateTime`

Access type: Read

Qualifiers: [not\_null]

The time that the Microsoft Defender for Endpoint agent last connected to the cloud.

`OnboardingState` Data type: `UInt32`

Access type: Read

Qualifiers: [not\_null]

The onboarding state.

`OrgId` Data type: `String`

Access type: Read

Qualifiers: [not\_null]

The ID of the organization that the Microsoft Defender for Endpoint agent reports to.

`ResourceID` Data type: `UInt32`

Access type: Read

Qualifiers: [key, not\_null]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

`SenseIsRunning` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

Indicates whether the Microsoft Defender for Endpoint agent is running.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).