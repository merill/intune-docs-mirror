---
layout: Conceptual
title: UpdateOptionalComponents Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/updateoptionalcomponents-method-in-class-sms_bootimagepackage
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
description: The UpdateOptionalComponents WMI class method updates all specified optional components to the boot image package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 49b2bc6f-9bc9-24d5-3721-ef6c81619d5c
document_version_independent_id: e369f2fb-8ff9-3439-d744-dd56cce5ef0c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/updateoptionalcomponents-method-in-class-sms_bootimagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/updateoptionalcomponents-method-in-class-sms_bootimagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/updateoptionalcomponents-method-in-class-sms_bootimagepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3178388e-2767-80d1-5954-6555f88eb548
---

# UpdateOptionalComponents Method - Configuration Manager | Microsoft Learn

The `UpdateOptionalComponents` Windows Management Instrumentation (WMI) class method, in Configuration Manager, updates all specified optional components to the boot image package.

Note

It is necessary to refresh the distribution points when using this method.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 UpdateOptionalComponents(
      String ComponentIds[],
);
```

#### Parameters

`ComponentIds` Data type: `String` Array

Qualifiers: [in]

Component identifiers. The following are possible values:

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
| 23 | Not used. |
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
| 49 | Not used. |
| 50 | WinPE-WDS-Tools.cab |
| 51 | WinPE-WinReCfg.cab |
| 52 | WinPE-WMI.cab |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

It is not necessary to refresh the distribution points when using this method.

For more information about NAL paths, see [SMS_NAL_Methods Server WMI Class](../misc/sms_nal_methods-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).