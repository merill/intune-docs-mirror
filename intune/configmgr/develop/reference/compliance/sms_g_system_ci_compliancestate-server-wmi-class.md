---
layout: Conceptual
title: SMS_G_System_CI_ComplianceState Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_g_system_ci_compliancestate-server-wmi-class
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
description: In Configuration Manager, the SMS_G_System_CI_ComplianceState Windows Management Instrumentation class is an SMS Provider server class that represents hardware inventory class objects for the compliance state of a configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1d9c742a-ec75-da81-67c2-0d9e6749f564
document_version_independent_id: ad2df94e-aec8-809d-fbc0-550dd320cab5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_g_system_ci_compliancestate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_g_system_ci_compliancestate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_g_system_ci_compliancestate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3b1ca600-1b2c-2539-b347-39b5f088ee09
---

# SMS_G_System_CI_ComplianceState Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_CI_ComplianceState` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents hardware inventory class objects for the compliance state of a configuration item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_CI_ComplianceState : SMS_G_System
{
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIVersion;
      UInt32 ComplianceState;
      String ComplianceStateName;
      UInt32 DesiredState;
      UInt32 IsApplicable;
      UInt32 IsDetected;
      UInt32 LastComplianceErrorID;
      String LocalizedDisplayName;
      UInt32 MaxNoncomplianceCriticality;
      UInt32 ResourceID;
      UInt32 SDMPackageVersion;
      UInt32 UserID;
      String UserName;
};
```

## Methods

The `SMS_G_System_CI_ComplianceState` class does not define any methods.

## Properties

`CI_ID` Data type: `Uint32`

Access type: Read

Qualifiers: [key]

The unique ID of the configuration item. This ID is unique only for the site.

`CI_UniqueID` Data type: `String`

Access type: Read

Qualifiers: None

The unique ID of the configuration item. This ID is unique across sites.

`CIVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Version of the configuration item.

`ComplianceState` Data type: `UInt32`

Access type: Read

Qualifiers: None

The compliance state of the computer for the specified configuration item.

`ComplianceStateName` Data type: `String`

Access type: Read

Qualifiers: None

The readable name of the compliance state. Possible values are:

| Value | Compliance state |
| --- | --- |
| 0 | Compliance State Unknown |
| 1 | Compliant |
| 2 | Non-Compliant |
| 4 | Error |

`DesiredState` Data type: `UInt32`

Access type: Read

Qualifiers: None

Desired state of the configuration item on the computer.

`IsApplicable` Data type: `Uint32`

Access type: Read

Qualifiers: None

Value indicating if the configuration item is applicable to the computer.

`IsDetected` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating if the configuration item is detected on the computer.

`LastComplianceErrorID` Data type: `UInt32`

Access type: Read

Qualifiers: None

ID of the last compliance status error.

`LocalizedDisplayName` Data type: `String`

Access type: Read

Qualifiers: None

Localized display name for the compliance state.

`MaxNoncomplianceCriticality` Data type: `UInt32`

Access type: Read

Qualifiers: None

The maximum noncompliance severity reported by the client for the configuration item.

`ResourceID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

See [SMS_G_System Server WMI Class](../core/clients/manage/sms_g_system_system-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read

Qualifiers: None

Version of the System Definition Model (SDM) package that is associated with the configuration item.

`UserID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the user.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the user.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class to update and determine the compliance state of the configuration item in the server database.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).