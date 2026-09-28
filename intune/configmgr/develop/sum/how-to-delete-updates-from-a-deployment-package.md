---
layout: Conceptual
title: Delete Updates from a Deployment Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-delete-updates-from-a-deployment-package
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
description: Remove update content from the existing software updates management package by using the RemoveContent method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: adaf415a-5bfb-f188-50a7-0ed9e280f37b
document_version_independent_id: dcd6af7a-af9c-76c5-ea3a-a934bb425b2b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-delete-updates-from-a-deployment-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-delete-updates-from-a-deployment-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-delete-updates-from-a-deployment-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: c345a414-5b0f-de0a-8300-cd3e587ebe89
---

# Delete Updates from a Deployment Package - Configuration Manager | Microsoft Learn

You remove updates from a software updates deployment package, in Configuration Manager, by obtaining an instance of the [SMS_SoftwareUpdatesPackage](../reference/sum/sms_softwareupdatespackage-server-wmi-class) class and using the [RemoveContent](../reference/sum/removecontent-method-in-class-sms_softwareupdatespackage) method.

### To delete updates from a software updates deployment package

1. Set up a connection to the SMS Provider.
2. Obtain an existing package object by using the `SMS_SoftwareUpdatesPackage` class.
3. Remove update content from the existing software updates management package by using the `RemoveContent` method.

## Example

The following example method shows how to remove updates from a software updates deployment package by using the `SMS_SoftwareUpdatesPackage` class and the `RemoveContent` method.

Important

No VBScript example was included, as the `RemoveContent` method does not return from the method call on failure. This is a known issue and is being investigated.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

Example of the method call in C#:

```csharp

// Prework for RemoveUpdatesfromSUMDeploymentPackage.
// Define the array of Content IDs to load into the content parameters.
int[] newArrayContentIDs2 = new int[] { 82 };

// Load the update content parameters into an object to pass to the method.
Dictionary<string, object> removeContentParameters = new Dictionary<string, object>();
removeContentParameters.Add("ContentIDs", newArrayContentIDs2);
removeContentParameters.Add("bRefreshDPs", true);

// Call the RemoveUpdatesfromSUMDeploymentPackage method.
RemoveUpdatesfromSUMDeploymentPackage(WMIConnection,
                                      "ABC00001",
                                      removeContentParameters);

```

```csharp

public void RemoveUpdatesfromSUMDeploymentPackage(WqlConnectionManager connection,
                                                  string existingSUMPackageID,
                                                  Dictionary<string, object> removeContentParameters)
{
    try
    {
        // Get the specific SUM Deployment Package to change.
        IResultObject existingSUMDeploymentPackage = connection.GetInstance(@"SMS_SoftwareUpdatesPackage.PackageID='" + existingSUMPackageID + "'");

        // Remove updates from the existing SUM Deployment Package using the RemoveContent method.
        // Note: The method will throw an exception, if the method is not able to add the content.
        IResultObject result = existingSUMDeploymentPackage.ExecuteMethod("RemoveContent", removeContentParameters);

        // Output a success message.
        Console.WriteLine("Removed content from the deployment package. ");

    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to remove content from the deployment package. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `existingSUMPackageID` | - Managed: `String` | The package ID for an existing software updates management package. |
| `removecontentParameters` | - Managed: `dictionary object` | The set of parameters (`ContentIDs`, `bRefreshDPs`) that is passed into the method and used with the `RemoveContent` method call. |

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