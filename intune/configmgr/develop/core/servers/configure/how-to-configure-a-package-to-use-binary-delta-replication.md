---
layout: Conceptual
title: Configure a Package to Use Binary Delta Replication - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-a-package-to-use-binary-delta-replication
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
description: Learn how to configure an existing package to use binary delta replication in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: dec91177-3a62-8ef8-897a-f21279beb646
document_version_independent_id: 467ac976-9d8f-ba70-7184-b4a0b5447c7c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-a-package-to-use-binary-delta-replication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-a-package-to-use-binary-delta-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-a-package-to-use-binary-delta-replication.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: cd64c706-5c02-4e6b-7593-bd8101314b6d
---

# Configure a Package to Use Binary Delta Replication - Configuration Manager | Microsoft Learn

The following example shows how to configure an existing package to use binary delta replication, in Configuration Manager, by using the `SMS_Package` class and the `PkgFlags` class property.

### To configure an existing package to use binary delta replication

1. Set up a connection to the SMS Provider.
2. Load the existing package object using `SMS_Package` class.
3. Modify the `PkgFlags` using the hexadecimal value for AP\_USE\_BINARY\_DELTA\_REP.
4. Save the package and the new package properties.

## Example

The following example method configures an existing package to use binary delta replication.

Important

The hexadecimal values that define the `PkgFlags` property are listed in the `SMS_Package` class reference material.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ModifyPackageToUseBinaryDeltaReplication(connection, existingPackageID)

    ' Define a constant with the hexadecimal value for AP_USE_BINARY_DELTA_REP.
    Const AP_USE_BINARY_DELTA_REP = &H04000000

    ' Get the specific advertisement instance to modify.     Dim packageToModify
    Set packageToModify = connection.Get("SMS_Package.PackageID='" & existingPackageID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:   " & packageToModify.Name
    Wscript.Echo "Package Flags:  " & packageToModify.PkgFlags

    ' Set the new property value.
    packageToModify.PkgFlags = packageToModify.PkgFlags OR AP_USE_BINARY_DELTA_REP

    ' Save the advertisement.
    packageToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Values after change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:   " & packageToModify.Name
    Wscript.Echo "Package Flags:  " & packageToModify.PkgFlags

End Sub

```

```c

public void ModifyPackageToUseBinaryDeltaReplication(WqlConnectionManager connection, string existingPackageID)
{
    // Define a constant with the hexadecimal value for AP_USE_BINARY_DELTA_REP.
    const Int32 AP_USE_BINARY_DELTA_REP = 0x04000000;

    try
    {
        // Get the specific package instance to modify.
        IResultObject packageToModify = connection.GetInstance(@"SMS_Package.PackageID='" + existingPackageID + "'");

        // List the existing property values.
        Console.WriteLine();
        Console.WriteLine("Values before change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:  " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags: " + packageToModify["PkgFlags"].IntegerValue);

        // Modify the PkgFlags value to include the AP_USE_BINARY_DELTA_REP value.
        packageToModify["PkgFlags"].IntegerValue = packageToModify["PkgFlags"].IntegerValue | AP_USE_BINARY_DELTA_REP;

        // Save the package with the new value.
        packageToModify.Put();

        // Reload the package to verify the change.
        packageToModify.Get();

        // List the existing (modified) property values.
        Console.WriteLine();
        Console.WriteLine("Values after change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:  " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags: " + packageToModify["PkgFlags"].IntegerValue);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to modify package. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
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