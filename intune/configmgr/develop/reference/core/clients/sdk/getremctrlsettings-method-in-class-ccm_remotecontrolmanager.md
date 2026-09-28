---
layout: Conceptual
title: GetRemCtrlSettings Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getremctrlsettings-method-in-class-ccm_remotecontrolmanager
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
description: The GetRemCtrlSettings Windows Management Instrumentation (WMI) class method in Configuration Manager that gets the remote control settings on a client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 518405aa-326e-a3b6-d060-ba8a7589dc48
document_version_independent_id: 30fbe0f7-92c4-f7aa-a658-fc109a24d0fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/getremctrlsettings-method-in-class-ccm_remotecontrolmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/getremctrlsettings-method-in-class-ccm_remotecontrolmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/getremctrlsettings-method-in-class-ccm_remotecontrolmanager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 29971a08-2fd8-7a77-6ea1-3d7aab9ee67d
---

# GetRemCtrlSettings Method - Configuration Manager | Microsoft Learn

The `GetRemCtrlSettings` Windows Management Instrumentation (WMI) class method in Configuration Manager that gets the remote control settings on a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 GetRemCtrlSettings
{
    [IN]    UInt32 RemoteControlSettingsLoc
    [OUT]   Boolean AllowClientChange
    [OUT]   Boolean UseLocalSettings
    [OUT]   Boolean RemoteControlEnabled
    [OUT]   Boolean AllowRemCtrlToUnattended
    [OUT]   Boolean PermissionRequired
    [OUT]   UInt32 AccessLevel
    [OUT]   UInt32 AudibleSignal
    [OUT]   Boolean ConnectionBar
    [OUT]   Boolean TaskbarIcon
};
```

## Parameters

`RemoteControlSettingsLoc` Data type: `UInt32`

Qualifiers: [id("0"), in]

RemoteControlSettingsLoc.

`AllowClientChange` Data type: `Boolean`

Qualifiers: [id("1"), out]

`true` if users can change policy or notification settings in Software Center.

`UseLocalSettings` Data type: `Boolean`

Qualifiers: [id("2"), out]

`true` if Remote Assistance settings, which the user can configure in a Control Panel program, is going to get overridden by the Configuration Manager settings.

`RemoteControlEnabled` Data type: `Boolean`

Qualifiers: [id("3"), out]

`true` if the remote control agent is enabled.

`AllowRemCtrlToUnattended` Data type: `Boolean`

Qualifiers: [id("4"), out]

`true` if the user should be prompted for permission to remote control the computer.

`PermissionRequired` Data type: `Boolean`

Qualifiers: [id("5"), out]

`true` if permission is required before starting a remote control session.

`AccessLevel` Data type: `UInt32`

Qualifiers: [id("6"), out]

Access level allowed. Possible values are:

| Value | Access level |
| --- | --- |
| 0 | No access |
| 1 | View only |
| 2 | Full control |

`AudibleSignal` Data type: `UInt32`

Qualifiers: [id("7"), out]

Value indicating if a control beep should be sounded during a remote control session to signify that the computer is being remotely controlled. This is only for Remote Control, not Remote Assistance. Possible values are:

| Value | Remote control beep |
| --- | --- |
| 0 | None |
| 1 | Beginning and end of session |
| 2 | Repeatedly |

`ConnectionBar` Data type: `Boolean`

Qualifiers: [id("8"), out]

`true` to show the session connection bar.

`TaskbarIcon` Data type: `Boolean`

Qualifiers: [id("9"), out]

`true` to show the session notification icon on the taskbar.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).