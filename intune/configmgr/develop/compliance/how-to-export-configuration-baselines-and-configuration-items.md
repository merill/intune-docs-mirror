---
layout: Conceptual
title: Export Configuration Baselines and Items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-export-configuration-baselines-and-configuration-items
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: You can export a configuration baseline or configuration item by using Configuration Manager SDK and reading the relevant SMS_ConfigurationItem instance and writing the SDMPackageXML property (string) to a file.
locale: en-us
document_id: a9443e3f-a729-5e25-51a5-1dd2873c009c
document_version_independent_id: 23c75375-e051-428c-9fc1-c3b4beb557b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/how-to-export-configuration-baselines-and-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/how-to-export-configuration-baselines-and-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/how-to-export-configuration-baselines-and-configuration-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: edb485b2-9e20-bbd5-d260-5b4a4f82288f
---

# Export Configuration Baselines and Items - Configuration Manager | Microsoft Learn

In Configuration Manager, to export a configuration baseline or configuration item using the Configuration Manager SDK, read the relevant `SMS_ConfigurationItem` instance and write the `SDMPackageXML` property (string) to a file.

Important

The encoding of the XML file must be set to UTF-16 encoded Unicode.

### To export Configuration Baselines and Configuration Items

1. Set up a connection to the SMS Provider.
2. Get the specific instance of [SMS_ConfigurationItem](../reference/compliance/sms_configurationitem-server-wmi-class) class using the unique ID of the configuration item (CI\_ID).
3. Copy the configuration item XML (SDMPackageXML) into a variable.
4. Write the configuration item XML content to a file.

## Example

The following code example shows how to read an instance of a configuration baseline or configuration item and then export it to a file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub DCMExportBaselineOrCI(swbemServices, _
                          pathToFile,    _
                          configurationItemId)

' Set required variables.
fileContents          =    ""
configurationItemXML  =    null

' Get specified configuration item (configurationItemId variable).
Set getCIInfo = swbemServices.Get("SMS_ConfigurationItem.CI_ID=" & configurationItemId )

' Copy configuration item XML into variable.
configurationItemXML = getCIInfo.SDMPackageXML

Wscript.Echo configurationItemXML

' Open file for write (Unicode option enabled by second true).
Set FSO = CreateObject("Scripting.FileSystemObject")
Set textFile = FSO.CreateTextFile(pathToFile, true, true)

' Write XML content to file specified by pathToFile.
textFile.Write configurationItemXML
textFile.Close

Wscript.Echo " "
Wscript.Echo "Successfully wrote " & pathToFile

End Sub

```

```c

public void DCMExportBaselineOrCI(WqlConnectionManager connection,
                                  string pathToOutputFile,
                                  string configurationItemId)
{

    // Set required variables.
    string configurationItemXML = null;

    try
    {
        // Get the specified configuration item (configurationItemId variable).
        IResultObject getCIInfo = connection.GetInstance(@"SMS_ConfigurationItem.CI_ID=" + configurationItemId);

        // Copy configuration item XML into variable.
        configurationItemXML = getCIInfo["SDMPackageXML"].StringValue;
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to retrieve configuration item xml. " + "\n" + ex.Message);
        throw;
    }

    StreamWriter sw = null;
    try
    {
        // Open file for output.
        sw = new StreamWriter(pathToOutputFile, false, System.Text.Encoding.Unicode);

        // Write XML to output file.
        sw.Write(configurationItemXML);
    }
    catch (Exception ex)
    {
        Console.WriteLine("Failed to write configuration item XML to: " + pathToOutputFile + "\n" + ex.Message);
        throw;
    }
    finally
    {
        if (sw != null)
        {
            sw.Close();
        }
    }

    Console.WriteLine("Wrote configuration item XML to: " + pathToOutputFile);
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| - pathToOutputFile- pathToFile | - Managed: `String`- VBScript: `String` | Path to the output file. |
| `configurationItemId` | - Managed: `String`- VBScript: `String` | Identifier of a configuration item to export. |

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