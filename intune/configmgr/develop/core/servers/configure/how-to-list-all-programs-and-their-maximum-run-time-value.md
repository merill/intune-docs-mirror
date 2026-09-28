---
layout: Conceptual
title: List All Programs and Their Maximum Run Time Value - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-list-all-programs-and-their-maximum-run-time-value
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
description: Learn how to list all programs with their maximum run time values by using the SMS_Package and SMS_Program classes and class properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 1b7005e1-631d-6d17-d8bd-59536115d671
document_version_independent_id: c7f454a5-bd57-945b-32c3-22caaf427df6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-list-all-programs-and-their-maximum-run-time-value.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-list-all-programs-and-their-maximum-run-time-value
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-list-all-programs-and-their-maximum-run-time-value.md
cmProducts: []
platformId: 562dd14a-e735-8e75-2587-df737f421a23
---

# List All Programs and Their Maximum Run Time Value - Configuration Manager | Microsoft Learn

In Configuration Manager, you can list all programs with their maximum run time values by using the `SMS_Package` and `SMS_Program` classes and class properties.

### To list all programs and their maximum run times

1. Set up a connection to the SMS Provider.
2. Load the available packages by using the `SMS_Package` class.
3. Enumerate through each set of programs using the `SMS_Program` class and the `PackageID` property from each package.
4. Output the package name, program name, and maximum run time value for each program.

## Example

The following example method shows how to list all programs, with corresponding package name, program name, and maximum run times.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ListPackagesProgramsandMaximumRunTimeValue(connection)
    Const wbemFlagReturnImmediately = 16    Const wbemFlagForwardOnly = 32    Dim packageQuery    Dim allPackages    Dim package    Dim packageID    Dim program    Dim programsForPackage
    ' Build query to get all of the packages.
    packageQuery = "SELECT * FROM SMS_Package"

    ' Run query.
    Set allPackages = connection.ExecQuery(packageQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection of package objects that needs to be enumerated.
    For Each package In allPackages

        ' Output package name and get the PackageID value to use in program query.
        WScript.Echo ""
        WScript.Echo "Package: "  & package.Name
        packageID = package.PackageID

        ' Build query to get the programs for the package.
        packageQuery = "SELECT * FROM SMS_Program WHERE PackageID='" & packageID & "'"

        ' Run query.
        Set programsForPackage = connection.ExecQuery(packageQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

        ' The query returns a collection of program objects that needs to be enumerated.
        For Each program In programsForPackage

            ' Output Maximum Runtime Value for each program found.
            WScript.Echo "  Program: "  & program.ProgramName
            WScript.Echo "  Maximum Runtime Value: "  & program.Duration

        Next
    Next

End Sub

```

```c

public void ListPackagesProgramsandMaximumRunTimeValue(WqlConnectionManager connection)
{
    try
    {
        // Build query to get the packages.
        string packageQuery = "SELECT * FROM SMS_Package";

        // Load the specific program to change (programname is a key value and must be unique).
        IResultObject allPackages = connection.QueryProcessor.ExecuteQuery(packageQuery);

        // The query returns a collection of packages that needs to be enumerated.
        foreach(IResultObject package in allPackages)
        {
            // Output package name and get the PackageID value to use in program query.
            Console.WriteLine();
            Console.WriteLine("Package: "  + package["Name"].StringValue);
            string packageID = package["PackageID"].StringValue;

            // Build query to get the programs for the package.
            string programQuery = "SELECT * FROM SMS_Program WHERE PackageID='" + packageID + "'";

            // Load the all programs belonging to the package.
            IResultObject programsForPackage = connection.QueryProcessor.ExecuteQuery(programQuery);

            // The query returns a collection of programs that needs to be enumerated.
            foreach(IResultObject program in programsForPackage)
            {
                // Output Maximum Runtime Value for each program found.
                Console.WriteLine("   Program: "  + program["ProgramName"].StringValue);
                Console.WriteLine("   Maximum Runtime Value: "  + program["Duration"].IntegerValue);
            }
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to list the packages and programs. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

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