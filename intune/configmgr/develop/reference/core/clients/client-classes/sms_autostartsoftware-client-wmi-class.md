---
layout: Conceptual
title: SMS_AutoStartSoftware Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_autostartsoftware-client-wmi-class
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
description: The SMS_AutoStartSoftware class is a client Windows Management Instrumentation (WMI) class that enumerates software that starts automatically with the operating system.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ba908333-e08d-09f4-5c30-09cb077aee07
document_version_independent_id: f068749e-8b2e-223c-61aa-0d4ebc6e9b3a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_autostartsoftware-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_autostartsoftware-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_autostartsoftware-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c764b672-6bd1-94a9-9ebf-33e8713c6406
---

# SMS_AutoStartSoftware Class - Configuration Manager | Microsoft Learn

The `SMS_AutoStartSoftware` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that enumerates software that starts automatically with, or immediately after, the operating system.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AutoStartSoftware
{
      String BinFileVersion;
      String BinProductVersion;
      String Description;
      String FileName;
      String FilePropertiesHash;
      String FilePropertiesHashEx;
      String FileVersion;
      String Location;
      String Product;
      String ProductVersion;
      String Publisher;
      String StartupType;
      String StartupValue;
};
```

## Methods

The `SMS_AutoStartSoftware` class does not define any methods.

## Properties

`BinFileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`BinProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: None

File description to be presented to users, for example, "Keyboard driver for AT-style keyboards" or "Microsoft Word for Windows".

`FileName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the file, including the extension but excluding the path, for example, "Notepad.exe".

`FilePropertiesHash` Data type: `String`

Access type: Read-only

Qualifiers: [key]

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, and `FileName` properties of the file.

`FilePropertiesHashEx` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, `FileName`, `FileVersion`, `BinProductVersion`, and `BinFileVersion` properties of the file.

`FileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the file, for example, "3.00A" or "5.00.RC2".

`Location` Data type: `String`

Access type: Read-only

Qualifiers: None

The path where the autostart file was discovered. This path is relative to the value of the `StartupType` property. For example, it can be "Software\Microsoft\Windows\CurrentVersion\Run" when the `StartupType` property is set to "HKEY\_LOCAL\_MACHINE".

`Product` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the product with which the file is distributed, for example, "Microsoft Windows".

`ProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the product with which the file is distributed, for example, "3.00A" or "5.00.RC2".

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: None

The company that produced the file, for example, "Microsoft Corporation" or "Standard Microsystems Corporation, Inc.".

`StartupType` Data type: `String`

Access type: Read-only

Qualifiers: None

The point from which the software is automatically launched. Possible values are:

- Registry:Current User
- Registry:Local Machine
- Win.ini
- All Users Startup Folder
- User Profile Startup Folder

    `StartupValue` Data type: `String`

    Access type: Read-only

    Qualifiers: None

    The application command string that is associated with the shortcut.

## Remarks

Much system-dependent software is loaded separately from the system due to the nature of the application. Most software requires the operating system to be running before being loaded. Along with many applications intended for useful purposes, such as sound driver, mouse driver, and other interfaces, items such as malware and viruses tend to place themselves within the same load areas. You can enumerate these applications to monitor the health of some of their security policies and procedures.

There are eight areas in the registry where applications can be run at the startup of the operating system. Enumeration of the following keys provides a list of applications and their associated paths from which header information can be retrieved:

- HKEY\_CURRENT\_USER\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY\_CURRENT\_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKEY\_CURRENT\_USER\Software\Microsoft\Windows\CurrentVersion\RunOnceEx
- HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\Windows\run
- HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\Windows\load
- HKEY\_LOCAL\_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY\_LOCAL\_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKEY\_LOCAL\_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnceEx

    The `SMS_AutoStartSoftware` class enumerates all items in the %*systemdir*%\Win.ini file, to identify older applications in addition to malicious software that might use this nontraditional method of activation. This class enumerates applications in the following file entries:
- win.ini [windows] run=
- win.ini [windows] load=

    The `SMS_AutoStartSoftware` class enumerates the contents of the **Startup** folder in the **Start** menu to provide the path to the binaries from which header information can be retrieved. If the binary is Rundll32.exe or Rundll64.exe, then the class retrieves the header information from the DLL file that is the first command line parameter for execution of Rundll32.exe.

    For example:

```
RUNDLL32.EXE C:\WINDOWS\System32\NvCpl.dll,NvStartup
```

In this case, the class gathers the header information from NVCpl.dll, instead of Rundll32.exe.

Note

If the header data for the executable file is `null` for the company, product, or version field, then the file name in uppercase is substituted for the field.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).