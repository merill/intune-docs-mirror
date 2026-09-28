---
layout: Conceptual
title: Create a Program - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-program
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
ms.date: 2020-03-23T00:00:00.0000000Z
description: In Configuration Manager, the following example shows how to create a program by using the SMS_Program class and class properties.
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 79d79722-3abc-58a6-75a8-8cf044ddd0e5
document_version_independent_id: 1f94513d-640d-ffb5-3999-14ab354829e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-program.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-program
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-program.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eccc57b3-2470-377c-7053-67399d671412
---

# Create a Program - Configuration Manager | Microsoft Learn

The following example shows how to create a program, in Configuration Manager, by using the `SMS_Program` class and class properties.

Important

Any advertised program will fail to run when the maintenance windows that are defined on the client computer are set for a period that is less than that program's **Maximum allowed run time setting**. For more information, see Program Run Scenario Using Maintenance Windows in the Configuration Manager documentation.

### To create a program

1. Set up a connection to the SMS Provider.
2. Create the new program object by using the `SMS_Program` class.
3. Populate the new program properties.

    Tip

    When you create a program for a Task Sequence or a Virtual Application Package, the SMS\_Program properties must be set to specific values. The following tables outline what those settings should be configured to.

    Task Sequence

    | Property Name | Property Value |
    | --- | --- |
    | ProgramName | \* |

    Virtual Application Package

    | Property Name | Property Value |
    | --- | --- |
    | CommandLine | PkgGUID={E742FFD6-D539-42CC-9827-73535FC81E06}:VersionGUID={19366289-8C55-44E2-A5EC-7B385EFB4C30}**Note:** The GUID values are taken from the virtual application's XML manifest file. |
    | ProgramName | [Virtual application] |
4. Save the new program and properties.

## Example

The following example method creates a new program and populates its properties for use in software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub CreateProgram(connection, existingPackageID, newProgramName, newProgramComment, newProgramCommandLine, newMaxRunTime)

    ' Create the new program object.    Dim newProgram
    Set newProgram = connection.Get("SMS_Program").SpawnInstance_

    ' Populate the program properties.
    newProgram.PackageID = existingPackageID
    newProgram.ProgramName = newProgramName
    newProgram.Comment = newProgramComment
    newProgram.CommandLine = newProgramCommandLine
    newProgram.Duration = newMaxRunTime

    ' Save the new program and properties.
    newProgram.Put_

    ' Output new program name.
    wscript.echo "Created program: " & newProgramName

End Sub
```

```c
public void CreateProgram(WqlConnectionManager connection,
                          string existingPackageID,
                          string newProgramName,
                          string newProgramComment,
                          string newProgramCommandLine,
                          int newMaxRunTime)
{
    try
    {
        // Create an instance of SMS_Program.
        IResultObject newProgram = connection.CreateInstance("SMS_Program");

        // Populate basic program values.
        newProgram["PackageID"].StringValue = existingPackageID;
        newProgram["ProgramName"].StringValue = newProgramName;
        newProgram["Comment"].StringValue = newProgramComment;
        newProgram["CommandLine"].StringValue = newProgramCommandLine;
        newProgram["Duration"].IntegerValue = newMaxRunTime;

        // Save the new program instance and values.
        newProgram.Put();

        Console.WriteLine("Created program: " + newProgramName);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create program. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`- VBScript: `String` | The name of the package associated with the program. |
| `newProgramName` | - Managed: `String`- VBScript: `String` | The name for the new program. |
| `newProgramComment` | - Managed: `String`- VBScript: `String` | Comment that describes the program in the Configuration Manager console. |
| `newProgramCommandLine` | - Managed: `String`- VBScript: `String` | The command line that runs when the program is launched. |
| `newMaxRunTime` | - Managed: `Integer`- VBScript: `Integer` | The approximate duration, in minutes, of program execution on the client computer. This parameter can have a max value of 720 minutes or 12 hours. |

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