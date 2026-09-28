---
layout: Conceptual
title: Import Configuration Baselines and Items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-import-configuration-baselines-and-configuration-items
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
description: In Configuration Manager, importing a configuration baseline or configuration item by using the Configuration Manager SDK requires a properly formatted XML file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 73bac49d-d5ad-d711-86dd-19cfbfcc7f9b
document_version_independent_id: 1f267f68-f1fd-2554-428c-8537d5b43941
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/how-to-import-configuration-baselines-and-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/how-to-import-configuration-baselines-and-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/how-to-import-configuration-baselines-and-configuration-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 771d2db9-e2d7-bda6-58cd-10266e2cb1a7
---

# Import Configuration Baselines and Items - Configuration Manager | Microsoft Learn

In Configuration Manager, importing a configuration baseline or configuration item by using the Configuration Manager SDK requires a properly formatted XML file. Unlike the Configuration Manager console, the Configuration Manager SDK does not support directly importing a CAB file.

Important

The encoding of the XML file must be set to UTF-16 encoded Unicode. The XML encoding can be identified in the XML header:

`<?xml version="1.0" encoding="utf-16" ?>`

When configuration data is imported into Configuration Manager, the format can be the following:

- DCM Digest XML only

### To import Configuration Baselines and Configuration Items

1. Set up a connection to the SMS Provider.
2. Read the source XML file into a variable.
3. Create an instance the `SMS_ConfigurationItem` class.
4. Copy the source file contents (XML) into the `SMS_ConfigurationItem` property `SDMPackageXML`.
5. Save the configuration item instance.

## Example

The following code examples show how to create an instance of a configuration baseline or a configuration item and then populate it by importing a configuration baseline or a configuration item XML definition.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub DCMImportBaselineOrCI(swbemServices,   _
                          pathToFile)

' Set required variables.
readFile = 1  'constant
fileContents          =    ""
initialReadSucceeded  =    ""
triStateTrue = -1  ' This sets the file read to Unicode.

' Check if source xml file exists.
set fileSytemObject = CreateObject("Scripting.FileSystemObject")
If fileSytemObject.FileExists(pathToFile) Then
    set textFile = fileSytemObject.OpenTextFile(pathToFile, readFile, False, triStateTrue)
    fileContents = textFile.ReadAll
    textFile.Close

    initialReadSucceeded = true

    set textFile = Nothing

    Wscript.Echo " "
    Wscript.Echo "Successfully read " & pathToFile

Else
    initialReadSucceeded = false

    Wscript.Echo " "
    Wscript.Echo "File does not exist."
End If
set fileSytemObject = Nothing

If initialReadSucceeded Then

    On Error Resume Next

        ' Create an instance of configuration item.
        set newCI = swbemServices.Get("SMS_ConfigurationItem").SpawnInstance_()

        ' Copy specified file contents (XML) into SMS_ConfigurationItem property.
        newCI.SDMPackageXML = fileContents

        ' Save configuration item.
        newCI.Put_

        If Err.Number<>0 Then
            Wscript.Echo "Couldn't create configuration item."
            Wscript.Echo "Possible duplicate configuration item or invalid XML."
            Wscript.Quit
        End If
    On Error Goto 0
Else
    Wscript.Echo " "
    Wscript.Echo "Failed to create configuration item."
End If

End Sub

```

```c

public void DCMImportBaselineOrCI(WqlConnectionManager connection,
                                  string pathToFile)
{

    // Set required variables.
    string fileContents = null;
    bool initialReadSucceeded = false;

    // Load XML file using pathToFile variable.
    try
    {
        // Open the file specified by the pathToFile variable and read the contents into a string.
        using (StreamReader sr = new StreamReader(pathToFile, System.Text.Encoding.Unicode))
        {
            fileContents = sr.ReadToEnd();
        }

        Console.WriteLine("Successfully read " + pathToFile + ".");

        initialReadSucceeded = true;
    }
    catch (Exception ex)
    {
        Console.WriteLine("Unable to read " + pathToFile + "." + "\n" + ex.Message);
        throw;
    }

    // Run only if the initial read was successful.
    if (initialReadSucceeded)
    {
        try
        {
            // Create an instance of Configuration Item.
            IResultObject newCI = connection.CreateInstance("SMS_ConfigurationItem");

            // Copy specified file contents (XML) into SMS_ConfigurationItem property.
            newCI["SDMPackageXML"].StringValue = fileContents;

            // Save new SMS_ConfigurationItem object.
            newCI.Put();
        }
        catch (SmsException ex)
        {
            Console.WriteLine("Failed to create configuration item using " + pathToFile + ".");
            Console.WriteLine(ex.Details);
            throw;
        }
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| - `connection`- `swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| pathToFile | - Managed: `String`- VBScript: `String` | Path of the XML file to import. |

## Compiling the Code

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

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).