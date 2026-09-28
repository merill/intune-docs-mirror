---
layout: Conceptual
title: Configure Package Properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-package-properties
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
description: Learn how the following example shows how to configure the properties of an existing package, in Configuration Manager, by using the SMS_Package class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d1e6da3a-ff8f-232f-df59-93eb34750644
document_version_independent_id: 273fcfb9-f200-fa59-441c-fd94b7302fb2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-package-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-package-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-package-properties.md
cmProducts: []
platformId: dff7f12b-5f7f-4760-a81a-8f9103004b51
---

# Configure Package Properties - Configuration Manager | Microsoft Learn

The following example shows how to configure the properties of an existing package, in Configuration Manager, by using the `SMS_Package` class.

### To configure an existing package

1. Set up a connection to the SMS Provider.
2. Load the existing package object by using `SMS_Package` class.
3. Populate any package properties (this example uses package description).
4. Save the package and the new package properties.

## Example

The following example method configures package properties for software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigurePackageProperties(connection, existingPackageID, newPackageDescription)

    ' Get the specific package object.     Dim packageToConfigure
    Set packageToConfigure = connection.Get("SMS_Package.PackageID='" & existingPackageID & "'")

    ' Replace the existing package property (in this case the package description).
    packageToConfigure.Description = newPackageDescription

    ' Save the package with the modified properties.
    packageToConfigure.Put_

    ' Output package ID and package name.
    wscript.echo "Configured Package "
    wscript.echo "Package ID:        "  & packageToConfigure.PackageID
    wscript.echo "Package Name:      "  & packageToConfigure.Name

End Sub

```

```c

public void ConfigurePackageProperties(WqlConnectionManager connection, string existingPackageID, string newPackageDescription)
{
    try
    {
        // Get specific package instance to modify.
        IResultObject packageToConfigure = connection.GetInstance(@"SMS_Package.PackageID='" + existingPackageID + "'");

        // Replace the existing package property with the new value (in this case the package description).
        packageToConfigure["Description"].StringValue = newPackageDescription;

        // Save package and modified package properties.
        packageToConfigure.Put();

        // Output package ID and package name.
        Console.WriteLine("Configured Package ");
        Console.WriteLine("Package ID:        " + packageToConfigure["PackageID"].StringValue);
        Console.WriteLine("Package Name:      " + packageToConfigure["Name"].StringValue);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to configure package. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`- VBScript: `String` | The ID of the existing package. |
| `newPackageDescription` | - Managed: `String`- VBScript: `String` | The description for the new package. |

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