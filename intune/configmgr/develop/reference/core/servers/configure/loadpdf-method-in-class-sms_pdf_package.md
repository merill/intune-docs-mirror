---
layout: Conceptual
title: LoadPDF Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package
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
description: Learn how to use the LoadPDF method to import a specified package definition file into the package definition file store.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6a418c64-eacb-de0c-d2e7-6574c1bf5de1
document_version_independent_id: e6ccce0f-4f57-2ad8-90a6-6c5bc042a097
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bb594fec-6118-7e99-28de-bc2a562e3fdb
---

# LoadPDF Method - Configuration Manager | Microsoft Learn

The `LoadPDF` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports a specified package definition file into the package definition file store.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 LoadPDF(
     String PDFFileName,
     String PDFFile,
     UInt32 PDFID,
     String RequiredIconNames[]
);
```

#### Parameters

`PDFFileName` Data type: `String`

Qualifiers: [in,SizeLimit("100")]

Full path and file name of the package definition file. The SMS Provider copies the file to the \Smsinstalldir\Scripts\&lt;localeid&gt;\Pdfstore\&lt;pdfid&gt; directory and replaces the .pdf file name extension with an .sms file name extension.

`PDFFile` Data type: `String`

Qualifiers: [in]

Text of the package definition file itself.

`PDFID` Data type: `UInt32`

Qualifiers: [out]

Assigned package definition file ID.

`RequiredIconNames` Data type: `String` Array

Qualifiers: [out]

List of icons referenced by the package definition file that must be loaded separately through the [LoadIconForPDF Method in Class SMS_PDF_Package](loadiconforpdf-method-in-class-sms_pdf_package) method.

## Return Values

An `SInt32` data type that indicates 0 for success or one of the following bit field warning flags for failure.

| Flag | Description |
| --- | --- |
| WARN\_BAD\_RUN (0) | Invalid run information specified. |
| WARN\_BAD\_RESTART (1) | Invalid restart information specified. |
| WARN\_BAD\_CANRUNWHEN (2) | Invalid CanRunWhen information specified. |
| WARN\_BAD\_ASSIGNMENT (3) | Invalid assignment information specified. |
| WARN\_BAD\_DEPENDPROG (4) | Invalid DependentProgram information specified. |
| WARN\_BAD\_SPECIFYDRIVE (5) | Invalid SpecifyDrive information specified. |
| WARN\_BAD\_ESTDISKSPACE (6) | Invalid EstimatedDiskSpace information specified. |
| WARN\_NO\_SUPPCLINFO (7) | No SupportedClients information specified. |
| WARN\_BAD\_SUPPCLINFO (8) | Invalid SupportedClients information specified. |
| WARN\_VER1PDF (9) | Version 1.0 file used. |
| WARN\_REMPRONOUKEY(10) | The remove program is set but no uninstall key is given. |

## Remarks

When your application imports a package definition file that has the same `Name`, `Publisher`, `Version`, and `Language` properties as an existing package definition file, the existing package definition file is overwritten, including the file icons and programs. The value specified in the `PDFID` parameter is retained.

## Example Code

The following example shows how to load a package definition file into the package definition file package store.

```
Const ForReading = 1

Dim fs, f                         ' File system object and file object.
Dim clsPDF As SWbemObject         ' SMS_PDF_Package class definition.
Dim ReturnCode As Long            ' Return code value from LoadPDF method.
Dim PDFID As Long                 ' Package definition file identifier generated from LoadPDF.
Dim PDFContent As String          ' Package definition file file content.
Dim ReqIconNames() As Variant     ' Required icon names from LoadPDF.
Dim Icon() As Byte                ' Icon used as input to LoadIconForPDF method.
Dim i, j As Integer
Dim FileSize As Integer           ' Size of the icon file.

Set Services = GetObject("winmgmts:\root\sms\<sitecode>")

' Open the package definition file file and read the content into a string.
Set fs = CreateObject("Scripting.FileSystemObject")
Set f = fs.OpenTextFile(<path\filename>, ForReading)
PDFContent = f.ReadAll
f.Close

' Load the package definition file into the package definition file store. Use the PDFID and ReqIconNames
' Variables in the LoadIconForPDF method.
Set clsPDF = Services.Get("SMS_PDF_Package")
ReturnCode = clsPDF.LoadPDF(<path\filename>, _
                            PDFContent, _
                            PDFID, _
                            ReqIconNames)

' You must load all the icons for the package definition file if the package definition file contains icons.
For i = LBound(ReqIconNames) To UBound(ReqIconNames)
    Open <path> & ReqIconNames(i) For Binary Access Read As #1
    FileSize = LOF(1) - 1
    ReDim Icon(FileSize)
    For j = 0 To FileSize
        Get #1, , Icon(j)
    Next
    Close #1

    clsPDF.LoadIconForPDF PDFID, ReqIconNames(i), Icon
Next
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).