---
layout: Conceptual
title: Create a Computer Variable - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-computer-variable
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
description: Create a computer variable for a computer that is running Configuration Manager by adding instances of SMS_MachineVariable to the SMS_MachineSettings class MachineVariables array property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 295ee8fc-9a14-a3e7-b382-a2f35da2016f
document_version_independent_id: 56f051ba-46dd-3e3d-cd82-a7a48e1f6f36
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-a-computer-variable.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-a-computer-variable
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-a-computer-variable.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 2be5c3fb-c7e8-36d2-c4aa-7aface94c264
---

# Create a Computer Variable - Configuration Manager | Microsoft Learn

You create a computer variable for a computer that is running Configuration Manager by adding instances of [SMS_MachineVariable](../reference/osd/sms_machinevariable-server-wmi-class) to the [SMS_MachineSettings](../reference/osd/sms_machinesettings-server-wmi-class) class `MachineVariables` array property.

### To create a computer variable

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get an instance of `SMS_MachineSettings`.
3. For each variable to be added, add instances of the embedded object a `SMS_MachineVariable` to the `MachineVariables` array property.
4. Commit the changes to the `SMS_MachineSettings` class instance.

## Example

The following example method creates a collection variable and adds it to the collection identified by the supplied identifier.

In the example, the `LocaleID` property is hard-coded to English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub CreateComputerVariable(connection, siteCode, name, value, mask, computerId)

    Dim computerSettings
    Dim computerVariables
    Dim computerVariable
    Dim Settings

    ' See if the computer settings object already exists. if it does not, create it.
    Set settings = connection.ExecQuery _
      ("Select * From SMS_MachineSettings Where ResourceID = '" & computerID & "'")

    If settings.Count = 0 Then
        Wscript.Echo "Creating computer settings object"
        Set computerSettings = connection.Get("SMS_MachineSettings").SpawnInstance_
        computerSettings.ResourceID = computerId
        computerSettings.SourceSite = siteCode
        computerSettings.LocaleID = 1033
        computerSettings.Put_
    End If

    ' Get the computer settings object.
    Set computerSettings = connection.Get("SMS_MachineSettings.ResourceID='" & computerId &"'" )

    ' Get the computer variables.
    computerVariables=computerSettings.MachineVariables

    ' Create and populate a new computer variable.
    Set computerVariable = connection.Get("SMS_MachineVariable").SpawnInstance_
    computerVariable.Name = name
    computerVariable.Value = value
    computerVariable.IsMasked = mask

    ' Add the new computer variable.
    ReDim Preserve computerVariables (UBound (computerVariables)+1)
    Set computerVariables(UBound(computerVariables)) = computerVariable

    computerSettings.MachineVariables=computerVariables

    computerSettings.Put_

 End Sub
```

```c
public void CreateComputerVariable(
    WqlConnectionManager connection,
    string siteCode,
    string name,
    string value,
    bool mask,
    int computerId)
{
    try
    {
        // Get the computer settings.
        IResultObject computerSettings=null;

        IResultObject computerSettingsQuery = connection.QueryProcessor.ExecuteQuery(
            "Select * from SMS_MachineSettings where ResourceId = '" + computerId + "'");

        foreach (IResultObject settings in computerSettingsQuery)
        {
            computerSettings = settings;
        }

        if (computerSettings == null) // It does not exist, so create it.
        {
            computerSettings = connection.CreateInstance(@"SMS_MachineSettings");
            computerSettings["ResourceID"].IntegerValue = computerId;
            computerSettings["SourceSite"].StringValue = siteCode;
            computerSettings["LocaleID"].IntegerValue = 1033;
            computerSettings.Put();
            computerSettings.Get();
        }

        // Create the computer variable.
        List<IResultObject> computerVariables = computerSettings.GetArrayItems("MachineVariables");
        IResultObject computerVariable = connection.CreateEmbeddedObjectInstance("SMS_MachineVariable");
        computerVariable["Name"].StringValue = name;
        computerVariable["Value"].StringValue = value;
        computerVariable["IsMasked"].BooleanValue = mask;

        // Add the computer variable to the computer settings.
        computerVariables.Add(computerVariable);
        computerSettings.SetArrayItems("MachineVariables", computerVariables);

        computerSettings.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create computer variable: " + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code of the source site. |
| `name` | - Managed: `String`- VBScript: `String` | The name of the variable to be created. |
| `value` | - Managed: `String`- VBScript: `String` | The value of the variable. |
| `mask` | - Managed: `Boolean`- VBScript: `Boolean` | Specifies whether the value is displayed in the Configuration Manager console.`true` - the variable value is not displayed.`false` - the variable value is displayed. |
| `computerID` | - Managed: `Integer`- VBScript: `Integer` | The computer identifier. Typically this is the [SMS_R_System](../reference/core/clients/manage/sms_r_system-server-wmi-class) class `ResourceID` property. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).