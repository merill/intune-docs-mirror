---
layout: Conceptual
title: OS deployment CreateMedia.exe - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-createmedia.exe
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
description: Create OS deployment media from the command-line or through a script.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
ms.custom: sfi-ropc-nochange
locale: en-us
document_id: 8a071107-6a4a-eaf5-68bc-9afea0c215cd
document_version_independent_id: 76c228be-68ac-5055-d9da-ffa1e3a7c722
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/operating-system-deployment-createmedia.exe.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/operating-system-deployment-createmedia.exe
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/operating-system-deployment-createmedia.exe.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 4363de96-f374-06bf-8be5-cb1d78bb3ffa
---

# OS deployment CreateMedia.exe - Configuration Manager | Microsoft Learn

Use `CreateMedia.exe` binary to create media from the command-line or through a script.

## Requirements

- Install the Configuration Manager console on the computer used to create media from the command-line or a script.
- Run `CreateMedia.exe` with required parameters from the folder: `%SMS_ADMIN_UI_PATH%`
- All content referenced by the selected type of media needs to be on one of the distribution points identified on the command-line:

    - Boot image package
    - OS image package
    - Software packages
    - Drivers
    - Applications referenced by the task sequence
    - A pre-execution package used during media execution

## Additional information

- If you specify it on the command line, you need a valid PKI certificate. When you don't specify a PKI certificate, the site uses a self-signed certificate with a default expiration date. The default is one year from the current date and time, unless you specify the dates as additional parameters.
- You need the following objects and associated package IDs:

    - Task sequence
    - Boot image
    - OS image
    - Pre-execution package
- Task sequence variables used to specify the management point on the command line.

    - For dynamic media:

        `"SMSTSLocationMPs= http://server1.contoso.net*http://server2.contoso.net"`

        Note

        `*` is a separator symbol.
    - For static based media:

        `"SMSTSMP= http://server.contoso.net"`

        Important

        Correctly specify whether the prefix is `http://` or `https://`
- When you run the `CreateMedia.exe` program, it immediately returns to the command prompt. View the `CreateTsMedia.log` file to monitor progress.
- Command-line parameters aren't case sensitive.

## Parameters for boot media

| **Parameter** | **Value** | **Comment** |
| --- | --- | --- |
| `/K:` | `mylabel` | Label used to specify the boot media type |
| `/P:` | `server.contoso.net` | FQDN of SMS Provider |
| `/S:` | `MCM` | Configuration Manager site code |
| `/C:` | `"Username=Administrator,Domain=MyDomain,Password=password"` | Optional credentials |
| `/D:` | `server1.contoso.net; server2.contoso.net` | One or more distribution point FQDN names, separated by a semicolon |
| `/L:` | `Configuration Manager` | Media text label |
| `/E:` | `MCM00009` | Optional pre-execution package ID |
| `/G:` | `cmd.exe` | Optional pre-execution command-line |
| `/Y:` | `4BootIt^` | Optional media password |
| `/R:` | `c:\cert\certificate.file` | Optional certificate file path |
| `/W:` | `qY249^i5we5X` | Certificate file password |
| `/U:` | `true` or `false` | Unknown machine support |
| `/J:` | `true` or `false` | Internet client |
| `/Z:` | `true` or `false` | User interaction |
| `/1:` | Long integer; long integer | SS certificate start time (HIGH;LOW) |
| `/2:` | Long integer; long integer | SS certificate expire time (HIGH;LOW) |
| `/5:` | `0` | UDA setting, integer as a string |
| `/X:` | `SMSTSMP=server.contoso.net` | Task sequence variable, in the form name=value |
| `/B:` | `MCM00002` | Boot image ID |
| `/T:` | `CD`, `UDF`, or `UDF+FORMAT` | Media type |
| `/F:` | `c:\file.iso` | Path for capture media file |

## Parameters for capture media

| Parameter | Example value | Comment |
| --- | --- | --- |
| `/K:` | `mylabel` | Label used to specify the capture media type |
| `/P:` | `server.contoso.net` | FQDN of SMS Provider |
| `/S:` | `MCM` | Configuration Manager site code |
| `/C:` | `"Username=Administrator,Domain=MyDomain,Password=password"` | Optional credentials |
| `/D:` | `server1.contoso.net; server2.contoso.net` | One or more distribution point FQDN names, separated by a semicolon |
| `/L:` | `Configuration Manager` | Media text label |
| `/B:` | `MCM00002` | Boot image ID |
| `/T:` | `CD`, `UDF`, or `UDF+FORMAT` | Media type |
| `/F:` | `c:\file.iso` | Path for capture media file |

## Parameters for stand-alone media

| Parameter | Example value | Comment |
| --- | --- | --- |
| `/K:` | `mylabel` | Label used to specify the standalone media type |
| `/P:` | `server.contoso.net` | FQDN of SMS Provider |
| `/S:` | `MCM` | Configuration Manager site code |
| `/C:` | `"Username=Administrator,Domain=MyDomain,Password=password"` | Optional credentials |
| `/D:` | `server1.contoso.net; server2.contoso.net` | One or more distribution point FQDN names, separated by a semicolon |
| `/L:` | `Configuration Manager` | Media text label |
| `/E:` | `MCM00009` | Optional pre-execution package ID |
| `/G:` | `cmd.exe` | Optional pre-execution command-line |
| `/Y:` | `4BootIt^` | Optional media password |
| `/A:` | `MCM00007` | Task sequence ID |
| `/T:` | `CD`, `UDF`, or `UDF+FORMAT` | Media type |
| `/Z:` | `true` or `false` | User interaction |
| `/X:` | `SMSTSMP=server.contoso.net` | Task sequence variable, in the form name=value |
| `/M:` | `4GB` | Size of selected media, units |
| `/F:` | `c:\file.iso` | Path for standalone media file |

## Parameters for pre-staged media

| Parameter | Example value | Comment |
| --- | --- | --- |
| `/K:` | `mylabel` | Label used to specify the prestaged media type |
| `/P:` | `server.contoso.net` | FQDN of SMS Provider |
| `/S:` | `MCM` | Configuration Manager site code |
| `/C:` | `"Username=Administrator,Domain=MyDomain,Password=password"` | Optional credentials |
| `/D:` | `server1.contoso.net; server2.contoso.net` | One or more distribution point FQDN names, separated by a semicolon |
| `/L:` | `Configuration Manager` | Media text label |
| `/3:` | `1.10.1.10` | Optional version text |
| `/4:` | `OEM scenario image` | Optional description text |
| `/E:` | `MCM00009` | Optional pre-execution package ID |
| `/G:` | `cmd.exe` | Optional pre-execution command-line |
| `/Y:` | `4BootIt^` | Optional media password |
| `/R:` | `c:\cert\certificate.file` | Optional certificate file path |
| `/W:` | `qY249^i5we5X` | Certificate file password |
| `/U:` | `true` or `false` | Unknown machine support |
| `/J:` | `true` or `false` | Internet client |
| `/Z:` | `true` or `false` | User interaction |
| `/1:` | Long integer; long integer | SS certificate start time (HIGH;LOW) |
| `/2:` | Long integer; long integer | SS certificate expire time (HIGH;LOW) |
| `/5:` | `0` | UDA setting, integer as a string |
| `/X:` | `SMSTSMP=server.contoso.net` | Task sequence variable, in the form name=value |
| `/B:` | `MCM00002` | Boot image ID |
| `/O:` | `MCM00006` | OS image ID |
| `/I:` | `1` | OS image index number |
| `/T:` | `HD` | Media type |
| `/F:` | `c:\file.iso` | Path for prestaged media file |