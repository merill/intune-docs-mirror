---
layout: Conceptual
title: Create a Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-package
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
description: Learn how to create a package in Configuration Manager by using the SMS_Package class and class properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b0900714-857d-4eb5-a1a4-7e6926ee9577
document_version_independent_id: fe44bc9a-a03f-00f0-e52f-1e8d8aeab3ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-package.md
cmProducts: []
platformId: e9fd8abc-ac92-a7af-2e3f-b849372c4b47
---

# Create a Package - Configuration Manager | Microsoft Learn

The following example shows how to create a package in Configuration Manager by using the `SMS_Package` class and class properties.

### To create a package

1. Set up a connection to the SMS Provider.
2. Create the new package object by using the `SMS_Package` class.
3. Populate the new package properties.

    Tip

    When you are creating a Virtual Application Package, you must set the `SMS_Package` properties to specific values. Instances of the `SMS_VirtualApp` class must reference instances of the `SMS_Package` class that use the properties described in the following table.

    Virtual Application Package

    | Property Name | Property Value |
    | --- | --- |
    | PackageType | 7 |
    | PkgSourceFlag | 2 |
    | PkgSourcePath | \\someserver\somesharepath |
4. Save the package.

## Example

The following example method creates a new package and populates its properties for use in software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub CreatePackage(connection, newPackageName, newPackageDescription, newPackageSourceFlag, newPackageSourcePath)

    ' Create the new package object.     Dim newPackage
    Set newPackage = connection.Get("SMS_Package").SpawnInstance_

    ' Populate the new package properties.
    newPackage.Name = newPackageName
    newPackage.Description = newPackageDescription
    newPackage.PkgSourceFlag = newPackageSourceFlag
    newPackage.PkgSourcePath = newPackageSourcePath

    ' Save the package.
    newPackage.Put_

    ' Output the new package name.
    wscript.echo "Created package: "  & newPackageDescription

End Sub
```

```c
public void CreatePackage(WqlConnectionManager connection, string newPackageName, string newPackageDescription, int newPackageSourceFlag, string newPackageSourcePath)
{
    try
    {
        // Create new package object.
        IResultObject newPackage = connection.CreateInstance("SMS_Package");

        // Populate new package properties.
        newPackage["Name"].StringValue = newPackageName;
        newPackage["Description"].StringValue = newPackageDescription;
        newPackage["PkgSourceFlag"].IntegerValue = newPackageSourceFlag;
        newPackage["PkgSourcePath"].StringValue = newPackageSourcePath;

        // Save new package and new package properties.
        newPackage.Put();

        // Output new package name.
        Console.WriteLine("Created package: " + newPackageName);
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
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newPackageName` | - Managed: `String`- VBScript: `String` | The name of the new package. |
| `newPackageDescription` | - Managed: `String`- VBScript: `String` | The description for the new package. |
| `newPackageSourceFlag` | - Managed: `Integer`- VBScript: `Integer` | The package source. |
| `newPackageSourcePath` | - Managed: `String`- VBScript: `String` | The path to the package source. |

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