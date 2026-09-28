---
layout: Conceptual
title: SMS_CH_Settings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_ch_settings-server-wmi-class
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
description: Learn how the SMS_CH_Settings class is an SMS Provider server class, in Configuration Manager, that represents client status settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e72d9313-c85a-580c-a227-7bcf1cfe3276
document_version_independent_id: 91fdda17-46ea-055d-2467-1676e79339c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/sms_ch_settings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/sms_ch_settings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/sms_ch_settings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: ceca9f48-5993-3f3d-e57a-e34eacae0670
---

# SMS_CH_Settings Class - Configuration Manager | Microsoft Learn

The `SMS_CH_Settings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents client status settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CH_Settings : SMS_BaseClass
{
    String ADRetrievingSchedule;
    UInt32 CleanUpInterval;
    UInt32 DDRInactiveInterval;
    UInt32 HWInactiveInterval;
    Boolean NeedADLastLogonTime;
    UInt32 PolicyInactiveInterval;
    UInt32 SettingsID;
    UInt32 StatusInactiveInterval;
    UInt32 SWInactiveInterval;
};
```

## Methods

The `SMS_CH_Settings` class does not define any methods.

## Properties

`ADRetrievingSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule for how frequently the system retrieves information from Active Directory.

`CleanUpInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

History clean up interval.

`DDRInactiveInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Heartbeat discovery inactive interval.

`HWInactiveInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Hardware inventory inactive interval.

`NeedADLastLogonTime` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Last logged on time from Active Directory.

`PolicyInactiveInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Policy request inactive interval.

`SettingsID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Settings ID.

`StatusInactiveInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Status message inactive interval.

`SWInactiveInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Software inventory inactive interval.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).