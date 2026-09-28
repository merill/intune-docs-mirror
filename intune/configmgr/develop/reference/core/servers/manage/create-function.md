---
layout: Conceptual
title: Create Function - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/create-function
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
description: The Create function creates a status MIF file that Configuration Manager uses to correlate the install status for an advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 27cf6e78-38b8-2cf6-1b53-db75222ec01a
document_version_independent_id: 358599d8-1c6c-6ee4-8fea-1344758ddd12
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/create-function.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/create-function
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/create-function.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: ce491d61-b846-6c0a-7f2b-e367517bc184
---

# Create Function - Configuration Manager | Microsoft Learn

The `Create` function creates a status MIF file that Configuration Manager uses to correlate the install status for an advertisement.

## Syntax

```
StatusMIF.Create(
     ByVal bstrFileName As String _
     ByVal bstrCompany As String _
     ByVal bstrProduct As String _
     ByVal bstrVersion As String _
     ByVal bstrLocale As String _
     ByVal bstrSerialNo As String _
     ByVal bstrMessage As String _
     ByVal bStatus As Long _
);
```

#### Parameters

`bstrFileName` Unique name for the MIF file. A file name extension must be .mif. The function writes the file to the %TEMP% directory.

`bstrCompany` Manufacturer or publisher of the product, for example, Microsoft. This parameter is limited to 64 characters.

`bstrProduct` Product or program name, for example, Office 2000. This parameter is limited to 64 characters.

`bstrVersion` Version of the product, for example, 8.0a. This parameter is limited to 64 characters.

`bstrLocale` Country/region or language code, for example, ENU. This parameter is optional and is limited to 16 characters.

`bstrSerialNo` Serial number of the product. This parameter is optional and is limited to 64 characters.

`bstrMessage` Descriptive message about the status of the installation, added to the program status message. This parameter is limited to 128 characters.

`bStatus``true` if the install status is success.

## Return Values

None.

## Remarks

Your installation (setup) application must create only one install status MIF file for the package. The file name must be unique so that multiple installations in a single session can report status without a conflict.

Installations that run on localized versions of Configuration Manager must specify values in the appropriate format: ANSI format for European languages; DBCS format for East Asia languages.

Your application must call `InstallStatusMIF` before the installation exits. The MIF file is not reported to Configuration Manager if the installation creates another process that calls `InstallStatusMIF`.

Note that the parameters `bstrFilename`, `bstrCompany`, `bstrProduct`, and `bstrVersion` are directly related to the [SMS_Package Server WMI Class](../configure/sms_package-server-wmi-class) properties `MIFFileName`, `MIFPublisher`, `MIFName`, and `MIFVersion`, respectively. These parameters and properties must contain the same values.

The example in the next section shows how to call the `Create` method.

## Example

```
[VisualBasic]
   Dim MIFStatus As New InstallStatusMIF

   MIFStatus.Create "MyStatusFile", _
                    "MyCompany", _
                    "MyProduct", _
                    "1.00.000", _
                    "ENU", _
                    " ", _
                    "Installation Successful", _
                    True
```

## Requirements

**Windows NT/2000**: Requires Windows NT 4.0 or later.

**Windows 95/98**: Requires Windows 95 or later.

**Version**: Requires SMS 2.0.

**Library**: Included as a resource in IsMIFCom.dll (Visual Basic).