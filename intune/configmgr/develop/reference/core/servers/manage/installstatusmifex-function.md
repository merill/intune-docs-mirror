---
layout: Conceptual
title: InstallStatusMIFEx Function - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/installstatusmifex-function
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
description: Learn how to enhance the functionality of InstallStatusMIF in Configuration Manager using InstallStatusMIFEx.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a535f488-2d42-ff22-472b-c9ced020ee39
document_version_independent_id: 0fb8d956-faeb-6194-5af2-676d2a1c767d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/installstatusmifex-function.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/installstatusmifex-function
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/installstatusmifex-function.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 661b0eab-9bea-3fc4-a38f-f81b187fe07f
---

# InstallStatusMIFEx Function - Configuration Manager | Microsoft Learn

The `InstallStatusMIFEx` function, in Configuration Manager, enhances the functionality of [InstallStatusMIF](installstatusmif-function).

## Syntax

```
DWORD InstallStatusMIFEx(
     char* pszFileName,
     char* pszCompany,
     char* pszProduct,
     char* pszVersion,
     char* pszLocale,
     char* pszSerialNo,
     char* pszMessage,
     BOOL bStatus,
     BOOL bProgramReboots
);
```

#### Parameters

`pszFileName` Pointer to a unique name for the Management Information Format (MIF) file. A file name extension must be .mif. The function writes the file to the %*TEMP*% directory.

`pszCompany` Pointer to the manufacturer or publisher of the product, for example, Microsoft. This parameter is limited to 64 characters.

`pszProduct` Pointer to the product or program name, for example, Microsoft Office 2000. This parameter is limited to 64 characters.

`pszVersion` Pointer to the version of the product, for example, 8.0a. This parameter is limited to 64 characters.

`pszLocale` Pointer to the country/region or language code, for example, ENU. This parameter is optional and limited to 16 characters.

`pszSerialNo` Pointer to the serial number of the product. This parameter is optional and limited to 64 characters.

`pszMessage` Pointer to a descriptive message about the status of the installation, which is added to the program status message. This parameter is limited to 128 characters.

`bStatus``true` if the install status is success.

`bProgramReboots``true` if the program will reboot the computer.

## Return Values

A non-zero value to indicate success.

## Remarks

`InstallStatusMIFEx` is functionally equivalent to `InstallStatusMIF`, except for the addition of the `bProgramReboot`parameter. Using `bProgramReboot`is the most reliable way of passing this information to Configuration Manager, because during reboot Configuration Manager might not be able to get the correct exit code from the process. If, after completing program execution, the program sets this flag in the MIF file and a reboot hasn't happened, Configuration Manager waits for one minute before launching any other program. This allows enough time for the reboot to finish. This flag also enables Configuration Manager to send a preliminary success status message for the program and then a final success status message after the reboot has occurred.

Your installation (setup) application must create only one install status MIF file for the package. The file name that you specify must be unique.

Installations that run on localized versions of Configuration Manager must specify values in the appropriate format: ANSI format for European languages; DBCS format for East Asia languages.

Your application must call `InstallStatusMIFEx` before the installation exits. The MIF file isn't reported to Configuration Manager if the installation creates another process that calls `InstallStatusMIFEx`.

The parameters `pszFilename`, `pszCompany`, `pszProduct`, and `pszVersion` are directly related to the [SMS_Package Server WMI Class](../configure/sms_package-server-wmi-class) properties `MIFFileName`, `MIFPublisher`, `MIFName`, and `MIFVersion`, respectively. These parameters and properties must contain the same values.

## Requirements

**Windows NT/2000**: Requires Windows 2000 or later.

**Version**: Requires SMS 2003 Advanced Client.

**Library**: Included as a resource in IsMIF32.dll (C/C++).