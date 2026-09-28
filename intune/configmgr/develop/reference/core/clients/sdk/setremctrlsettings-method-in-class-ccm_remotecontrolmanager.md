---
layout: Conceptual
title: SetRemCtrlSettings Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setremctrlsettings-method-in-class-ccm_remotecontrolmanager
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
description: The SetRemCtrlSettings WMI class method specifies the remote control settings on a client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fb041e12-8368-c8d9-5d40-d125e1676c43
document_version_independent_id: d7db9233-3e6e-d36d-38d0-fe6620494343
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/setremctrlsettings-method-in-class-ccm_remotecontrolmanager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/setremctrlsettings-method-in-class-ccm_remotecontrolmanager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/setremctrlsettings-method-in-class-ccm_remotecontrolmanager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9826436d-d7c2-db06-f22d-88ccafa0842a
---

# SetRemCtrlSettings Method - Configuration Manager | Microsoft Learn

The `SetRemCtrlSettings` Windows Management Instrumentation (WMI) class method in Configuration Manager that specifies the remote control settings on a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 SetRemCtrlSettings
{
    [IN]    Boolean UseLocalSettings
    [IN]    Boolean RemoteControlEnabled
    [IN]    Boolean AllowRemCtrlToUnattended
    [IN]    Boolean PermissionRequired
    [IN]    UInt32 AccessLevel
    [IN]    UInt32 AudibleSignal
    [IN]    Boolean ConnectionBar
    [IN]    Boolean TaskbarIcon
};
```

## Parameters

`UseLocalSettings` Data type: `Boolean`

Qualifiers: [id("0"), in]

`true` if Remote Assistance settings, which the user might configure in a Control Panel program, should be overridden by the Configuration Manager settings.

`RemoteControlEnabled` Data type: `Boolean`

Qualifiers: [id("1"), in]

`true` if the remote control agent is enabled.

`AllowRemCtrlToUnattended` Data type: `Boolean`

Qualifiers: [id("2"), in]

`true` if remote control of an unattended computer is allowed.

`PermissionRequired` Data type: `Boolean`

Qualifiers: [id("3"), in]

`true` if the user should be prompted for permission to remote control the computer.

`AccessLevel` Data type: `UInt32`

Qualifiers: [id("4"), in]

Access level allowed. Possible values are:

| Value | Access level |
| --- | --- |
| 0 | No access |
| 1 | View only |
| 2 | Full control |

`AudibleSignal` Data type: `UInt32`

Qualifiers: [id("5"), in]

Value indicating if a control beep should be sounded during a remote control session to signify that the computer is being remotely controlled. This beep is only for Remote Control, not Remote Assistance. Possible values are:

| Value | Remote control beep |
| --- | --- |
| 0 | None |
| 1 | Beginning and end of session |
| 2 | Repeatedly |

`ConnectionBar` Data type: `Boolean`

Qualifiers: [id("6"), in]

`true` to show the session connection bar.

`TaskbarIcon` Data type: `Boolean`

Qualifiers: [id("7"), in]

`true` to show the session notification icon on the taskbar.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).