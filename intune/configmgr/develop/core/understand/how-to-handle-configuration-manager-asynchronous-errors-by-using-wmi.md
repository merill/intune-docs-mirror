---
layout: Conceptual
title: Handle Asynchronous Errors by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi
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
description: In Configuration Manager, when an error occurs in an asynchronous call, the error object is passed as the second parameter to the `OnCompleted` method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ad489bdf-1bd9-65aa-187c-d69e712cfca4
document_version_independent_id: b12ebe38-6b13-8484-23ee-6c2d0e3417ee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 95572f6e-2ea8-c8a0-2198-428c126150a7
---

# Handle Asynchronous Errors by Using WMI - Configuration Manager | Microsoft Learn

In Configuration Manager, when an error occurs in an asynchronous call, the error object is passed as the second parameter to the `OnCompleted` method. Inside your `OnCompleted` implementation, you check the error object the same as you would for a synchronous call.

You determine if there is an error by checking the `HResult` parameter of the `OnCompleted` method.

## Example

This VBScript sample displays error information if there is a error during an asynchronous operation. To test, change the query to an invalid query such as `Select * From ?????`.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs

Sub sink_OnCompleted(HResult, oErr, oCtx)
    WScript.Echo "All collections returned"

    if HResult <> 0 Then
    ' Determine the type of error.
        If oErr.Path_.Class = "__ExtendedStatus" Then
            WScript.Echo "WMI Error: "& oErr.Description
        ElseIf ExtendedStatus.Path_.Class = "SMS_ExtendedStatus" Then
            WScript.Echo "Provider Error: "& oErr.Description
            WScript.Echo "Code: " & oErr.ErrorCode
        End If
    End If
    bdone = true
End sub

```

## .NET Framework Security

Using script to pass the user name and password is a security risk and should be avoided where possible.