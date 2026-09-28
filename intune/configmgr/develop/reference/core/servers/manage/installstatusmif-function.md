---
layout: Conceptual
title: InstallStatusMIF Function - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/installstatusmif-function
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
description: The InstallStatusMIF function creates a status Management Information Format (MIF) file that Configuration Manager uses to correlate the install status for an advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 57dcc37b-f537-6222-7dc8-711533adb673
document_version_independent_id: 3501fec6-f893-58ed-b103-47c545526bbd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/installstatusmif-function.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/installstatusmif-function
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/installstatusmif-function.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: e72c782d-d570-d698-510f-0b6079740518
---

# InstallStatusMIF Function - Configuration Manager | Microsoft Learn

The `InstallStatusMIF` function creates a status Management Information Format (MIF) file that Configuration Manager uses to correlate the install status for an advertisement.

## Syntax

```
DWORD InstallStatusMIF(
     char* pszFileName,
     char* pszCompany,
     char* pszProduct,
     char* pszVersion,
     char* pszLocale,
     char* pszSerialNo,
     char* pszMessage,
     BOOL bStatus
);
```

#### Parameters

`pszFileName` Pointer to a unique name for the MIF file. A file name extension must be .mif. The function writes the file to the %*TEMP*% directory.

`pszCompany` Pointer to the manufacturer or publisher of the product, for example, Microsoft. This parameter is limited to 64 characters.

`pszProduct` Pointer to the product or program name, for example, Microsoft Office 2000. This parameter is limited to 64 characters.

`pszVersion` Pointer to the version of the product, for example, 8.0a. This parameter is limited to 64 characters.

`pszLocale` Pointer to the country/region or language code, for example, ENU. This parameter is optional and is limited to 16 characters.

`pszSerialNo` Pointer to the serial number of the product. This parameter is optional and is limited to 64 characters.

`pszMessage` Pointer to a descriptive message about the status of the installation, added to the program status message. This parameter is limited to 128 characters.

`bStatus``true` if the install status is success.

## Return Values

A non-zero value to indicate success.

## Remarks

Your installation (setup) application must create only one install status MIF file for the package. The file name that you specify must be unique.

Installations that run on localized versions of Configuration Manager must specify values in the appropriate format: ANSI format for European languages; DBCS format for East Asia languages.

Your application must call `InstallStatusMIF` before the installation exits. The MIF file is not reported to Configuration Manager if the installation creates another process that calls `InstallStatusMIF`.

Note that the parameters `pszFilename`, `pszCompany`, `pszProduct`, and `pszVersion` are directly related to the [SMS_Package Server WMI Class](../configure/sms_package-server-wmi-class) properties `MIFFileName`, `MIFPublisher`, `MIFName`, and `MIFVersion`, respectively. These parameters and properties must contain the same values.

The `InstallStatusMIF` function is provided in a 32-bit version (Ismif32.dll) and a 16-bit version (Ismif16.dll). The appropriate DLL is installed on the client computer during the Configuration Manager client installation process.

The example in the next section shows how to call the `InstallStatusMIF` function by using the Ismif32.dll file directly. A failure to load the Ismif32.dll file might indicate that the system is not a Configuration Manager client.

## Example

```
[C/C++]
DWORD (WINAPI *InstallStatusMIF)(char *, char *, char *, char *, char *, char *, char *, BOOL);

#define PROCSIGNATURE DWORD (WINAPI *)(char *, char *, char *, char *, char *, char *, char *, BOOL)

    HINSTANCE  hinst;
    int  RetCode;

    hinst = LoadLibrary("ismif32.dll");

    InstallStatusMIF = (PROCSIGNATURE) GetProcAddress(hinst, "InstallStatusMIF");

    if (InstallStatusMIF)
    {
        RetCode = InstallStatusMIF("Status",
                                   "Microsoft",
                                   "Microsoft SQL Server 7.0",
                                   "7.00.000",
                                   "ENU",
                                   NULL,
                                   "Installation Successful",
                                   true);
    }
    FreeLibrary(hinst);
```

## Requirements

**Windows NT/2000**: Requires Windows NT 4.0 or later.

**Windows 95/98**: Requires Windows 95 or later.

**Version**: Requires SMS 2.0.

**Library**: Included as a resource in Ismif32.dll (C/C++); Ismif16.dll (C/C++).