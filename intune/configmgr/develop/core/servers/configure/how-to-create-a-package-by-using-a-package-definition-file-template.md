---
layout: Conceptual
title: Create a Package Using a Package Definition File Template - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template
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
description: The following example shows how to create a package and program by using a package definition file template in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bc08bfe7-1126-c801-77aa-cb882c2a2e51
document_version_independent_id: f2e40499-16ca-4008-cce4-e683e65cae3f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template.md
cmProducts: []
platformId: ad7dced6-9e43-6f2e-7b8c-3a2a76eed943
---

# Create a Package Using a Package Definition File Template - Configuration Manager | Microsoft Learn

The following example shows how to create a package and program by using a package definition file template in Configuration Manager. The package definition file template contains the default values that are used to create `SMS_Package` and `SMS_Program` objects. The following example uses the `SMS_PDF_Package` class and the `GetPDFData` method to load the package definition file template information and to create a package and the related programs.

### To create a package by using a package definition file template

1. Set up a connection to the SMS Provider.
2. Create the new package object by using the `SMS_PDF_Package` class.
3. Populate any additional package properties.
4. Load the program information and associate each program with the package.

## Example

The following example method creates a new package by using a package definition file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub SWDCreatePDFPackage(connection, existingPDF_ID, newPackageSourceFlag, newPackageSourcePath)
    ' The PDF_ID must be passed in.
    ' The PDF_ID can be identified through the SMS_PDF_Package class.

    Dim newPDFPackage
    Dim returnCode
    Dim newPackage
    Dim newPackagePath
    Dim packageID
    Dim program
    Dim arrayOfPrograms

    ' Package Creation
    ' ----------------
    ' Create new SMS_PDF_Package instance.
    Set newPDFPackage = connection.Get("SMS_PDF_Package")

    ' Load the Package Definition File data using the GetPDFData method.
    returnCode = newPDFPackage.GetPDFData(existingPDF_ID, newPackage, arrayOfPrograms)

    ' Assign any additional package properties.
    newPackage.PkgSourceFlag = newPackageSourceFlag
    newPackage.PkgSourcePath = newPackageSourcePath

    ' Save the package path and get the Package ID.
    Set newPackagePath = newPackage.Put_
    packageID = newPackagePath.Keys("PackageID")

    ' Program Creation
    ' -----------------
    ' Enumerate through the program array and create the programs.
    For Each program In arrayOfPrograms
        program.PackageID = packageID
        program.Put_
    Next

End Sub
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPDF_ID` | - VBScript: `Integer` | ID of the package definition file. |
| `newPackageSourceFlag` | - VBScript: `Integer` | The package source. |
| `newPackageSourcePath` | - VBScript: `String` | The path to the package source. |

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).