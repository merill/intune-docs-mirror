---
layout: Conceptual
title: Add Updates to a Deployment Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package
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
description: You add updates to a software updates deployment package, in Configuration Manager, by obtaining an instance of the SMS_SoftwareUpdatesPackage class and by using the AddUpdateContent method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d9e81875-1ee7-8013-698f-b239f6a4c79b
document_version_independent_id: 6b4a8fb1-94fb-0d1c-af17-6ae4d465564b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-add-updates-to-a-deployment-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 89a03c61-3d10-42e5-03b8-703458d5a530
---

# Add Updates to a Deployment Package - Configuration Manager | Microsoft Learn

You add updates to a software updates deployment package, in Configuration Manager, by obtaining an instance of the [SMS_SoftwareUpdatesPackage](../reference/sum/sms_softwareupdatespackage-server-wmi-class) class and by using the [AddUpdateContent](../reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) method.

### To create a software updates deployment package

1. Set up a connection to the SMS Provider.
2. Obtain an existing package object by using the `SMS_SoftwareUpdatesPackage` class.
3. Add update content to the existing package using the `AddUpdateContent` method.

## Example

The following example method shows how to add updates to a software updates deployment package by using the `SMS_SoftwareUpdatesPackage` class and the `AddUpdateContent` method.

Note

The updates must be available in the content source path (as part of the dictionary object `addUpdateContentParameters` in C#). If the updates exist in a package source, that package source cannot be used for more than one deployment package.

Important

No VBScript example was included, as the `AddUpdateContent` method does not return from the method call on failure. This is a known issue and is being investigated.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

Example of the method call in C#:

```csharp
// PREWORK FOR AddUpdatesToSUMDeploymentPackage

// Define the array of Content Ids to load into addUpdateContentParameters.
int[] newArrayContentIds = new int[] { 82 };

// Define the array of source paths (these must be UNC) to load into addUpdateContentParameters.
string[] newArrayContentSourcePath = new string[] { "\\\\ServerOne\\source1" };

// Load the update content parameters into an object to pass to the method.
Dictionary<string, object> addUpdateContentParameters = new Dictionary<string, object>();
addUpdateContentParameters.Add("ContentIds", newArrayContentIds);
addUpdateContentParameters.Add("ContentSourcePath", newArrayContentSourcePath);
addUpdateContentParameters.Add("bRefreshDPs", false);

AddUpdatestoSUMDeploymentPackage(WMIConnection,
                                 "ABC00001",
                                 addUpdateContentParameters);
```

```csharp
public void AddUpdatestoSUMDeploymentPackage(WqlConnectionManager connection,
                                            string existingSUMPackageID,
                                            Dictionary<string, object> addUpdateContentParameters)
{
    try
    {
        // Get the specific SUM Deployment Package to change.
        IResultObject existingSUMDeploymentPackage = connection.GetInstance(@"SMS_SoftwareUpdatesPackage.PackageID='" + existingSUMPackageID + "'");

        // Add updates to the existing SUM Deployment Package using the AddUpdateContent method.
        // Note: The method will throw an exception, if the method is not able to add the content.
        existingSUMDeploymentPackage.ExecuteMethod("AddUpdateContent", addUpdateContentParameters);

        // Output a success message that the content was added.
        Console.WriteLine("Added content to the SUM deployment package. ");
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to add content to the SUM deployment package.");
        Console.WriteLine("Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `existingSUMPackageID` | - Managed: `String` | The package ID for an existing software updates deployment package. |
| `addUpdateContentParameters` | - Managed: `dictionary` object | The set of parameters (`ContentIDs`, `ContentSourcePath`, `bRefreshDPs`) that is passed into the method and used with the `AddUpdateContent` method call. |

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