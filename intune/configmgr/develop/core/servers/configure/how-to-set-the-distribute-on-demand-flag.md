---
layout: Conceptual
title: Set the Distribute on Demand Flag - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-set-the-distribute-on-demand-flag
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
description: The following example shows how to set the "distribute on demand" flag property of an existing package by using the SMS_Package Server WMI Class class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 21a1b0d1-2594-733a-44ea-b2a5166388ae
document_version_independent_id: a6050e0b-ad5a-a152-a93f-0c29570483f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-set-the-distribute-on-demand-flag.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-set-the-distribute-on-demand-flag
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-set-the-distribute-on-demand-flag.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 6aa7fd59-9840-29c5-c5b3-7491a75d266a
---

# Set the Distribute on Demand Flag - Configuration Manager | Microsoft Learn

The following example shows how to set the "distribute on demand" flag property of an existing package by using the [SMS_Package Server WMI Class](../../../reference/core/servers/configure/sms_package-server-wmi-class) class in Configuration Manager.

### To set the distribute on demand flag

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Load the existing package object by using [SMS_Package Server WMI Class](../../../reference/core/servers/configure/sms_package-server-wmi-class) class.
3. Populate the package flag property.
4. Save the package and the new package properties.

## Example

The following example method sets the "distribute on demand" flag for a package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub SetDistributeOnDemandFlag(connection,         _
                              existingPackageID)

    ' Define a constant with the hexadecimal value for the DISTRIBUTE_ON_DEMAND.
    DISTRIBUTE_ON_DEMAND = &H40000000

    ' Get the specific package instance to modify.
    Set packageToModify = connection.Get("SMS_Package.PackageID='" & existingpackageID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:            " & packageToModify.Name
    Wscript.Echo "Package Flags (integer): " & packageToModify.PkgFlags

    ' Set the new property value.
    packageToModify.PkgFlags = packageToModify.PkgFlags OR DISTRIBUTE_ON_DEMAND

    ' Save the package.
    packageToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Values after change:  "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:             " & packageToModify.Name
    Wscript.Echo "Package Flags (integer):  " & packageToModify.PkgFlags

End Sub

```

```c

public void SetDistributeOnDemandFlag(WqlConnectionManager connection,
                                      string existingPackageID)
{
    // Define a constant with the hexadecimal value for DISTRIBUTE_ON_DEMAND.
    const Int32 DISTRIBUTE_ON_DEMAND = 0x40000000;

    try
    {
        // Get the specific package instance to modify.
        IResultObject packageToModify = connection.GetInstance(@"SMS_Package.PackageID='" + existingPackageID + "'");

        // List the existing property values.
        Console.WriteLine();
        Console.WriteLine("Values before change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:            " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags (integer): " + packageToModify["PkgFlags"].IntegerValue);

        // Modify the PkgFlags value to include the DISTRIBUTE_ON_DEMAND value.
        packageToModify["PkgFlags"].IntegerValue = packageToModify["PkgFlags"].IntegerValue | DISTRIBUTE_ON_DEMAND;

        // Save the package with the new value.
        packageToModify.Put();

        // Reload the package to verify the change.
        packageToModify.Get();

        // List the existing (modified) property values.
        Console.WriteLine();
        Console.WriteLine("Values after change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:            " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags (integer): " + packageToModify["PkgFlags"].IntegerValue);
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
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`- VBScript: `String` | The ID of the package. |

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).