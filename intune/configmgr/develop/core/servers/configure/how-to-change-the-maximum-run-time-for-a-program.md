---
layout: Conceptual
title: Change the Maximum Run Time for a Program - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-change-the-maximum-run-time-for-a-program
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
description: In Configuration Manager, the following example shows how to modify a program by using the SMS_Package and SMS_Program classes and properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a0108f9e-45e0-9acc-2ee6-395fb12370b5
document_version_independent_id: a41e8fb3-8583-2d83-3d53-7161e1ee7bb4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-change-the-maximum-run-time-for-a-program.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-change-the-maximum-run-time-for-a-program
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-change-the-maximum-run-time-for-a-program.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9af0cc4f-a4cc-0ef6-35af-306a5142efcf
---

# Change the Maximum Run Time for a Program - Configuration Manager | Microsoft Learn

The following example shows how to modify a program, in Configuration Manager, by using the `SMS_Package` and `SMS_Program` classes and properties.

Important

Any advertised program fails to run when the maintenance windows defined on the client computer are set for a period that is less than that program's `Maximum allowed run time setting`. See the topic "Program Run Scenario Using Maintenance Windows" in the Configuration Manager documentation for more information.

### To change the maximum run time for a program

1. Set up a connection to the SMS Provider.
2. Query for the programs associated with the existing package ID provided.
3. Enumerate through the programs until a match for the program name is found.
4. Replace the program maximum run time property with the one passed into the method.
5. Save the program object and properties.

## Example

The following example method changes the maximum run time for an existing program.

Note

A slight variation of this example could change property values for all of the programs associated with a specific package. For an example, see the [How to List All Programs and Their Maximum Run Time Value](how-to-list-all-programs-and-their-maximum-run-time-value) code example. However, for a more efficient method of accessing a specific program, using the `PackageID` and `ProgramName`, see the [How to Modify Program Properties](how-to-modify-program-properties) code example.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ModifyProgram(connection, existingpackageID, existingProgramNameToModify, newMaxRunTime)

    Const wbemFlagReturnImmediately = 16
    Const wbemFlagForwardOnly = 32
    Dim query
    Dim programsForPackage
    Dim program

    ' Build a query to get the programs for the package.
    query = "SELECT * FROM SMS_Program WHERE PackageID='" & existingPackageID & "'"

    ' Run the query.
    Set programsForPackage = connection.ExecQuery(query, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection that needs to be enumerated.
    For Each program In programsForPackage

        ' If a match for the program name is found, make the change(s).
        If program.ProgramName=existingProgramNameToModify Then

            ' Replace the existing package property (in this case the package description).
            program.Duration = newMaxRunTime

            ' Save the program with the modified properties.
            program.Put_

            ' Output program name.
            wscript.echo "Modified program: "  & program.ProgramName

            Exit For
        End If
    Next

End Sub
```

```c
public void ModifyProgram(WqlConnectionManager connection, string existingPackageID, string existingProgramNameToModify, int newMaxRunTime)
{

    try
    {
        // Build query to get the programs for the package.
        string query = "SELECT * FROM SMS_Program WHERE PackageID='" + existingPackageID + "'";

        // Load the specific program to change (programname is a key value and must be unique).
        IResultObject programsForPackage = connection.QueryProcessor.ExecuteQuery(query);

        // The query returns a collection that needs to be enumerated.
        foreach(IResultObject program in programsForPackage)
        {
            // If a match for the program name is found, make the change(s).
            if (program["ProgramName"].StringValue == existingProgramNameToModify)
            {
                 // Replace the existing package property (in this case the package description).
                 program["Duration"].IntegerValue = newMaxRunTime;

                 // Save the program with the modified properties.
                 program.Put();

                 // Output program name.
                 Console.WriteLine("Modified program: "  + program["ProgramName"].StringValue);
            }
        }

    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to modify the program. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`- VBScript: `String` | The ID of an existing package with which to associate the program. |
| `existingProgramNameToModify` | - Managed: `String`- VBScript: `String` | The name for the program to modify. |
| `newMaxRunTime` | - Managed: `Integer`- VBScript: `Integer` | New approximate duration, in minutes, of program execution on the client computer. |

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