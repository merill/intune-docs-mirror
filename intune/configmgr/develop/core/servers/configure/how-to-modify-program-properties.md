---
layout: Conceptual
title: Modify Program Properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-modify-program-properties
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
description: Learn how the following will modify a program, in Configuration Manager, by using the SMS_Package and SMS_Program classes and properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: df590a8f-56cb-0d31-d030-e074cddf376f
document_version_independent_id: 55fe1631-2817-80bb-1460-72450334c45f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-modify-program-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-modify-program-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-modify-program-properties.md
cmProducts: []
platformId: e80d0b6d-5679-439e-90b2-c879e85fc611
---

# Modify Program Properties - Configuration Manager | Microsoft Learn

The following example shows how to modify a program, in Configuration Manager, by using the `SMS_Package` and `SMS_Program` classes and properties.

### To modify program properties

1. Set up a connection to the SMS Provider.
2. Get the program instance using the package ID and program name provided.
3. Replace the program description property with the one passed into the method.
4. Save the program object and properties.

## Example

The following example method modifies program properties for software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ModifyProgram(connection, existingpackageID, existingProgramNameToModify, newProgramDescription)

     ' Load the specific program to change (programname is a key value and must be unique).     Dim program
     Set program = connection.Get("SMS_Program.PackageID='" & existingPackageID & "'" & ",ProgramName='" & existingProgramNameToModify & "'")

     ' Replace the existing program property (in this case the program description).
     program.Description = newProgramDescription
     program.Comment = newProgramDescription
     ' Save the program with the modified properties.
     program.Put_

     ' Output program name.
     WScript.echo "Modified program: " & program.ProgramName

End Sub

```

```c

public void ModifyProgram(WqlConnectionManager connection, string existingPackageID, string existingProgramNameToModify, string newProgramDescription)
{

    try
    {

        // Load the specific program to change (programname is a key value and must be unique).
        IResultObject program = connection.GetInstance(@"SMS_Program.PackageID='" + existingPackageID + "',ProgramName='" + existingProgramNameToModify + "'");

        // Replace the existing program property (in this case the program description).
        program["Description"].StringValue = newProgramDescription;
        program["Comment"].StringValue = newProgramDescription;
        // Save the program with the modified properties.
        program.Put();

        // Output program name.
        Console.WriteLine("Modified program: " + program["ProgramName"].StringValue);

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
| `newProgramDescription` | - Managed: `String`- VBScript: `String` | The description for the new program. |

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