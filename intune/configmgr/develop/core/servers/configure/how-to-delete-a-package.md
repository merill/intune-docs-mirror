---
layout: Conceptual
title: Delete a Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-delete-a-package
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
description: Learn how to delete a package in Configuration Manager using the SMS_Package class with the following example.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d4f82f24-c6f5-b75f-f055-1e6c59a2a987
document_version_independent_id: 660c383d-9708-b92c-c55c-ae233be41cb1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-delete-a-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-delete-a-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-delete-a-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ece5850e-8359-bfb4-42a2-6a5cb0db6ce2
---

# Delete a Package - Configuration Manager | Microsoft Learn

The following example shows how to delete a package in Configuration Manager by using the `SMS_Package` class.

Note

Any reference to this package, such as an advertisement or task sequence, should be cleaned up before deleting the package

### To delete a package

1. Set up a connection to the SMS Provider.
2. Load the existing package object by using the `SMS_Package` class.
3. Delete the package by using the delete method.

## Example

The following example method deletes an existing package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub DeleteAPackage(connection, existingPackageID)

    ' Get the specified package instance (passed in as existingPackageID).    Dim packageToDelete
    Set packageToDelete = connection.Get("SMS_Package.PackageID='" & existingPackageID & "'")

    ' Delete the package.
    PackageToDelete.Delete_

    ' Output package ID of deleted package.
    wscript.echo "Deleted Package ID: " & existingPackageID

End Sub
```

```c
public void DeleteAPackage(WqlConnectionManager connection, string existingPackageID)
{
    try
    {
        // Get the specified package instance (passed in as existingPackageID).
        IResultObject packageToDelete = connection.GetInstance(@"SMS_Package.PackageID='" + existingPackageID + "'");

        // Delete the package instance.
        packageToDelete.Delete();

        // Output package ID of deleted package.
        Console.WriteLine("Deleted Package ID: " + existingPackageID);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create package. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`- VBScript: `String` | The ID of the existing package. |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security