---
layout: Conceptual
title: Handle Synchronous Errors by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi
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
description: Handle synchronous errors by using the SWbemLastError object when an error occurs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 5dc5697b-7307-4780-6402-def91083905f
document_version_independent_id: d45eaa16-bc70-151a-4abe-23cf1f8476a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a3185cb-221a-4e17-9d7d-57120807d2e5
platformId: 1cea2db9-9ce5-b7db-71aa-c7dbf4c5350c
---

# Handle Synchronous Errors by Using WMI - Configuration Manager | Microsoft Learn

You handle synchronous errors, in Configuration Manager, by inspecting the `SWbemLastError` object when an error occurs. An error has occurred when the error object `Number` property is non-zero.

Note

In VBScript you should declare that you want to resume running the script if an error occurs. Otherwise, the script will end when an error condition occurs. To do this, use the `On Error Resume Next` declaration in your script.

## Example

The following VBScript example displays the most recent error information that is available from the `SWbemLastError` object. You can use the following code, which tries to get an invalid SMS\_Package package to test it.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs

Sub ExerciseError(connection)

    On Error Resume next

    Dim packages
    Dim package

    ' Run the query.
    Set package = connection.Get("SMS_Package.PackageID='UNKNOWN'")

    If Err.Number<>0 Then
        Call DisplayLastError
    End If

End Sub
```

```vbs

Sub DisplayLastError
    Dim ExtendedStatus

    ' Get the error object.
    Set ExtendedStatus = CreateObject("WbemScripting.SWBEMLastError")

    ' Determine the type of error.
    If ExtendedStatus.Path_.Class = "__ExtendedStatus" Then
        WScript.Echo "WMI Error: "& ExtendedStatus.Description
    ElseIf ExtendedStatus.Path_.Class = "SMS_ExtendedStatus" Then
        WScript.Echo "Provider Error: "& ExtendedStatus.Description
        WScript.Echo "Code: " & ExtendedStatus.ErrorCode
    End If
End Sub

```