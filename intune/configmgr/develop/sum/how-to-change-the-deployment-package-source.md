---
layout: Conceptual
title: Change the Deployment Package Source - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-change-the-deployment-package-source
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: You change the deployment package source for a software updates deployment package in Configuration Manager by obtaining an instance of the SMS_SoftwareUpdatesPackage class and using the ValidateNewPackageSource method.
locale: en-us
document_id: 9af6f2f0-8cd0-6ae7-6476-7c97d3fe0f06
document_version_independent_id: 99d76163-ffc5-d2c3-fcc5-8e97ba01156a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-change-the-deployment-package-source.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-change-the-deployment-package-source
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-change-the-deployment-package-source.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 97c8093c-ade8-d023-72e7-058fb6b6a33f
---

# Change the Deployment Package Source - Configuration Manager | Microsoft Learn

You change the deployment package source for a software updates deployment package, in Configuration Manager, by obtaining an instance of the [SMS_SoftwareUpdatesPackage](../reference/sum/sms_softwareupdatespackage-server-wmi-class) class and by using the [ValidateNewPackageSource](../reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage) method.

Note

The package source for most other types of packages can be changed in the console. However, this option is not available for software updates packages.

### To change the deployment package source

1. Set up a connection to the SMS Provider.
2. Obtain an existing package object by using the `SMS_SoftwareUpdatesPackage` class.
3. Verify the package source by using the `ValidateNewPackageSource` method.
4. Change the package source for an existing software updates deployment package by changing the `PkgSourcePath` property of the package.

## Example

The following example method shows how to change the deployment package source for a software updates deployment package by using the `SMS_SoftwareUpdatesPackage` class and the `ValidateNewPackageSource` method.

Note

All of the updates available in the old package source must be available in the new package source (the content source path, passed in as the `newPackageSourceLocation` variable in the below scripts).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

Example of the subroutine call in Visual Basic:

```vbscript

' PREWORK FOR ChangeDeploymentPackageSource

' Define the new package location to validate (package location must be UNC).
newPackageSourceLocation = "\\SMSSERVER\source1"

Call ChangeDeploymentPackageSource(swbemServices,             _
                                   "ABC00003",                _
                                   newPackageSourceLocation)

```

Example of the method call in C#:

```csharp

//PREWORK FOR ChangeDeploymentPackageSource.

// Define the new package location to validate (package location must be UNC).
string newPackageSourceLocation = "\\\\SMSSERVER\\source1";

// Load the validateNewPackageSource parameters into an object to pass to the method.
Dictionary<string, object> validateNewPackageSourceParameters = new Dictionary<string, object>();
validateNewPackageSourceParameters.Add("PackageSource", newPackageSourceLocation);

//The method call.
SUMSnippets.ChangeDeploymentPackageSource(WMIConnection,
                                          "ABC00003",
                                          validateNewPackageSourceParameters,
                                          newPackageSourceLocation);

```

```vbscript

Sub ChangeDeploymentPackageSource(connection,                   _
                                  existingSUMPackageID,         _
                                  newDeploymentPackageLocation)

    On Error Resume Next

    ' Get an existing SUM Deployment Package to change.
    Set existingSUMDeploymentPackage = connection.Get("SMS_SoftwareUpdatesPackage.PackageID='" & existingSUMPackageID & "'")

    ' Check the package source for the existing SUM Deployment Package using the ValidateNewPackageSource method.
    existingSUMDeploymentPackage.ValidateNewPackageSource(newDeploymentPackageLocation)

    ' Check the error information from the SWBemLasError object to determine success or failure of the ValidateNewPackageSource method.
    If Err.Number = 0 Then

        ' Output a success message if the new package location is valid.
        Wscript.Echo "The new location of the SUM deployment package validated. "
        Wscript.Echo "Updating the SUM deployment package with the new package location.  "

       ' Update the StoredPkgPath property of the existing deployment package
       ' with the new source location if the package location is valid.
       existingSUMDeploymentPackage.PkgSourcePath = newDeploymentPackageLocation

       ' Save the updated package deployment package.
       existingSUMDeploymentPackage.Put_

    Else

        ' Output a failure message if the new deployment package location is not valid.
        Wscript.Echo "The new location of the SUM deployment package failed to validate. "

    End If

 End Sub

```

```csharp

public void ChangeDeploymentPackageSource(WqlConnectionManager connection,
                                          string existingSUMPackageId,
                                          Dictionary<string, object> validateNewPackageSourceParameters,
                                          string newPackageSource)
{
    try
    {
        // Get the specific SUM Deployment Package to change.
        IResultObject existingSUMDeploymentPackage = connection.GetInstance(@"SMS_SoftwareUpdatesPackage.PackageId='" + existingSUMPackageId + "'");

        // Validate the existing SUM Deployment Package content using the ValidateContent method.
        // Note: The method will throw an exception, if the package source does not validate.
        existingSUMDeploymentPackage.ExecuteMethod("ValidateNewPackageSource", validateNewPackageSourceParameters);

        // Output a success message if the new package location is valid.
        Console.WriteLine("The new location of the SUM deployment package validated.  ");

        // Update the PkgSourcePath property of the existing deployment package with the new source location.
        existingSUMDeploymentPackage["PkgSourcePath"].StringValue = newPackageSource;

        // Save the package properties.
        existingSUMDeploymentPackage.Put();

        // Output a success message that the package location was updated.
        Console.WriteLine("Updated the SUM deployment package with the new package location.  ");
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to validate the new package source.");
        Console.WriteLine("Failed to update the SUM deployment package.");
        Console.WriteLine("Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingSUMPackageID` | - Managed: `String`- VBScript: `String` | The package ID for an existing software updates deployment package. |
| `validateNewPackageSource` | - Managed: `dictionary` object | The `validateNewPackageSource` is a dictionary object containing the parameters that the `ValidateNewPackageSource` method requires.`PackageSource` |
| `newPackageSourceLocation` | - Managed: `String`- VBScript: `String` | The new deployment package source location. The source path must be a Universal Naming Convention (UNC) path. All of the updates available in the old package source must be available in the new package source. |

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