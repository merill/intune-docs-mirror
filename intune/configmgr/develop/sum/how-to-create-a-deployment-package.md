---
layout: Conceptual
title: Create a Deployment Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-a-deployment-package
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
description: A software updates deployment package initiated by creating an instance of the SMS_SoftwareUpdatesPackage class and populating the properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4a8524eb-040f-22b6-d3c7-ac48be6882ac
document_version_independent_id: f8af957e-a5b6-17e1-10b3-78345849f4f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-create-a-deployment-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-create-a-deployment-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-create-a-deployment-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 90ddd93e-d37b-9422-24e8-3126124e8723
---

# Create a Deployment Package - Configuration Manager | Microsoft Learn

You create a software updates deployment package, in Configuration Manager, by creating an instance of the `SMS_SoftwareUpdatesPackage` class and populating the properties.

### To create a software updates deployment package

1. Set up a connection to the SMS Provider.
2. Create the new package object by using the `SMS_SoftwareUpdatesPackage` class.
3. Populate the new package properties.
4. Save the new package and properties.

## Example

The following example method shows how to create a software updates deployment package by using the `SMS_SoftwareUpdatesPackage` class and class properties.

Note

The package location must be unique, and the updates must be available in the package source.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

Example of the subroutine call in Visual Basic:

```vbscript

Call CreateSUMDeploymentPackage(swbemServices,                  _
                                "New SUM Deployment Package",   _
                                "New SUM Package Description",  _
                                2,                              _
                                "\\ServerOne\SUM_TestPackageSource")

```

Example of the method call in C#:

```csharp

SUMSnippets.CreateSUMDeploymentPackage(WMIConnection,
                                       "New SUM Deployment Package",
                                       "New SUM Package Description",
                                       2,
                                       "\\\\ServerOne\\SUM_TestPackageSource");
```

```vbscript

Sub CreateSUMDeploymentPackage(connection,                 _
                               newPackageName,             _
                               newPackageDescription,      _
                               newPackageSourceFlag,       _
                               newPackageSourcePath)

    ' Create the new SUM package object.
    Set newSUMDeploymentPackage = connection.Get("SMS_SoftwareUpdatesPackage").SpawnInstance_

    ' Populate the new SUM package properties.
    newSUMDeploymentPackage.Name = newPackageName
    newSUMDeploymentPackage.Description = newPackageDescription
    newSUMDeploymentPackage.PkgSourceFlag = newPackageSourceFlag
    newSUMDeploymentPackage.PkgSourcePath = newPackageSourcePath

    ' Save the new SUM package object and properties.
    newSUMDeploymentPackage.Put_

    ' Output the new SUM package name.
    Wscript.Echo "Created the new SUM Deployment Package: " & newPackageName

 End Sub

```

```csharp

public void CreateSUMDeploymentPackage(WqlConnectionManager connection,
                                       string newPackageName,
                                       string newPackageDescription,
                                       int newPackageSourceFlag,
                                       string newPackageSourcePath)

{
    try
    {
        // Create the new SUM package object.
        IResultObject newSUMDeploymentPackage = connection.CreateInstance("SMS_SoftwareUpdatesPackage");

        // Populate the new SUM package properties.
        newSUMDeploymentPackage["Name"].StringValue = newPackageName;
        newSUMDeploymentPackage["Description"].StringValue = newPackageDescription;
        newSUMDeploymentPackage["PkgSourceFlag"].IntegerValue = newPackageSourceFlag;
        newSUMDeploymentPackage["PkgSourcePath"].StringValue = newPackageSourcePath;

        // Save the new SUM package and new package properties.
        newSUMDeploymentPackage.Put();

        // Output the new SUM package name.
        Console.WriteLine("Created the new SUM Deployment Package: " + newPackageName);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create the SUM Deployment Package. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newDeploymentPackageName` | - Managed: `String`- VBScript: `String` | The new deployment package name. |
| `newDeploymentPackageDescription` | - Managed: `String`- VBScript: `String` | The description for the new deployment package. |
| `newPackageSourceFlag` | - Managed: `Integer`- VBScript: `Integer` | The new package source flag. |
| `newPackageSourcePath` | - Managed: `String`- VBScript: `String` | The new package source path. The package location must be unique and the updates must be available in the package source. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).