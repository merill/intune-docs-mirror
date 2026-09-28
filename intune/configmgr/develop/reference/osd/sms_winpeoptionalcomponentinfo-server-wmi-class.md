---
layout: Conceptual
title: SMS_WinPEOptionalComponentInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class
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
description: Represents WinPE optional components information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: eb682196-4798-c324-0a57-f2c6931089ca
document_version_independent_id: d4b520c8-f6ef-8b48-429b-7656e5b0c63b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: bec18283-33ae-6530-bca7-9a3c30e11bed
---

# SMS_WinPEOptionalComponentInfo Class - Configuration Manager | Microsoft Learn

The `SMS_WinPEOptionalComponentInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents WinPE optional components information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_WinPEOptionalComponentInfo : SMS_BaseClass
{
    String Architecture;
    String DependentComponentNames[];
    UInt32 DependentIds[];
    Boolean IsRequired;
    UInt32 LanguageID;
    String Name;
    String RelativePath;
    UInt64 Size;
    UInt32 UniqueID;
};
```

## Methods

The `SMS_WinPEOptionalComponentInfo` class does not define any methods.

## Properties

`Architecture` Data type: `String`

Access type: Read

Qualifiers: none

The architecture of WinPE optional components. Possible values are:

| Value |
| --- |
| X86 |
| X64 |

`DependentComponentNames` Data type: `String` Array

Access type: Read

Qualifiers: none

The name of dependent WinPE optional components.

`DependentIds` Data type: `UInt32` Array

Access type: Read

Qualifiers: none

The unique ID of dependent WinPE optional components.

`IsRequired` Data type: `Boolean`

Access type: Read

Qualifiers: none

`true` if the WinPE optional component is required.

`LanguageID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The language ID of the WinPE optional component.

`Name` Data type: `String`

Access type: Read

Qualifiers: none

The name of the WinPE optional component.

`RelativePath` Data type: `String`

Access type: Read

Qualifiers: none

The relative path to the Assessment and Deployment Kit (ADK) installation path of the WinPE optional component.

`Size` Data type: `UInt64`

Access type: Read

Qualifiers: none

The size of the WinPE optional component.

`UniqueID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The unique ID of WinPE optional component. Possible values are:

| ID value | WinPE component |
| --- | --- |
| X86 |  |
| 1 | WinPE-DismCmdlets.cab |
| 2 | WinPE-Dot3Svc.cab |
| 3 | WinPE-EnhancedStorage.cab |
| 4 | WinPE-FMAPI.cab |
| 5 | WinPE-FontSupport-JA-JP.cab |
| 6 | WinPE-FontSupport-KO-KR.cab |
| 7 | WinPE-FontSupport-ZH-CN.cab |
| 8 | WinPE-FontSupport-ZH-HK.cab |
| 9 | WinPE-FontSupport-ZH-TW.cab |
| 10 | WinPE-HTA.cab |
| 11 | WinPE-StorageWMI.cab |
| 12 | WinPE-LegacySetup.cab |
| 13 | WinPE-MDAC.cab |
| 14 | WinPE-NetFx4.cab |
| 15 | WinPE-PowerShell3.cab |
| 16 | WinPE-PPPoE.cab |
| 17 | WinPE-RNDIS.cab |
| 18 | WinPE-Scripting.cab |
| 19 | WinPE-SecureStartup.cab |
| 20 | WinPE-Setup.cab |
| 21 | WinPE-Setup-Client.cab |
| 22 | WinPE-Setup-Server.cab |
| 23 | N/A |
| 24 | WinPE-WDS-Tools.cab |
| 25 | WinPE-WinReCfg.cab |
| 26 | WinPE-WMI.cab |

| ID value | WinPE component |
| --- | --- |
| X64 |  |
| 27 | WinPE-DismCmdlets.cab |
| 28 | WinPE-Dot3Svc.cab |
| 29 | WinPE-EnhancedStorage.cab |
| 30 | WinPE-FMAPI.cab |
| 31 | WinPE-FontSupport-JA-JP.cab |
| 32 | WinPE-FontSupport-KO-KR.cab |
| 33 | WinPE-FontSupport-ZH-CN.cab |
| 34 | WinPE-FontSupport-ZH-HK.cab |
| 35 | WinPE-FontSupport-ZH-TW.cab |
| 36 | WinPE-HTA.cab |
| 37 | WinPE-StorageWMI.cab |
| 38 | WinPE-LegacySetup.cab |
| 39 | WinPE-MDAC.cab |
| 40 | WinPE-NetFx4.cab |
| 41 | WinPE-PowerShell3.cab |
| 42 | WinPE-PPPoE.cab |
| 43 | WinPE-RNDIS.cab |
| 44 | WinPE-Scripting.cab |
| 45 | WinPE-SecureStartup.cab |
| 46 | WinPE-Setup.cab |
| 47 | WinPE-Setup-Client.cab |
| 48 | WinPE-Setup-Server.cab |
| 49 | N/A |
| 50 | WinPE-WDS-Tools.cab |
| 51 | WinPE-WinReCfg.cab |
| 52 | WinPE-WMI.cab |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).