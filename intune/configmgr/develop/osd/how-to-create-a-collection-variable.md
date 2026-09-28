---
layout: Conceptual
title: Create a Collection Variable - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-collection-variable
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
description: Add instances of SMS_CollectionVariable Server WMI Class to the CollectionVariables property of SMS_CollectionSettings Server WMI Class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 5832ee6b-91fc-beed-86e4-13a982b33bec
document_version_independent_id: dc65e819-a850-dd10-cffb-3dd659bc8924
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-a-collection-variable.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-a-collection-variable
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-a-collection-variable.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 47c63811-602b-e7fb-94a1-638c0d3c86e5
---

# Create a Collection Variable - Configuration Manager | Microsoft Learn

You create a collection variable for a Configuration Manager collection by adding instances of [SMS_CollectionVariable Server WMI Class](../reference/osd/sms_collectionvariable-server-wmi-class) to the `CollectionVariables` property of [SMS_CollectionSettings Server WMI Class](../reference/core/clients/collections/sms_collectionsettings-server-wmi-class).

### To create a collection variable

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get an instance of [SMS_CollectionSettings](../reference/core/clients/collections/sms_collectionsettings-server-wmi-class).
3. For each variable to be added, add instances of the embedded object [SMS_CollectionVariable](../reference/osd/sms_collectionvariable-server-wmi-class) to the *CollectionVariables* array property.
4. Commit the changes to the `SMS_CollectionSettings` class instance.

## Example

The following example method creates a collection variable and adds it to the collection identified by the supplied identifier. If the `SMS_CollectionSettings` object for the collection does not exist, it is created.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub CreateCollectionVariable( connection, name, value, mask, collectionId, precedence)

    Dim collectionSettings
    Dim collectionVariables
    Dim collectionVariable
    Dim Settings

    ' See if the settings collection already exists. if it does not, create it.
    Set settings = connection.ExecQuery _
      ("Select * From SMS_CollectionSettings Where CollectionID = '" & collectionID & "'")

    If settings.Count = 0 Then
        Wscript.Echo "Creating collection settings object"
        Set collectionSettings = connection.Get("SMS_CollectionSettings").SpawnInstance_
        collectionSettings.CollectionID = collectionId
        collectionSettings.Put_
    End If

    ' Get the collection settings object.
    Set collectionSettings = connection.Get("SMS_CollectionSettings.CollectionID='" & collectionId &"'" )

    ' Get the collection variables.
    collectionVariables=collectionSettings.CollectionVariables

    ' Create and populate a new collection variable.
    Set collectionVariable = connection.Get("SMS_CollectionVariable").SpawnInstance_
    collectionVariable.Name = name
    collectionVariable.Value = value
    collectionVariable.IsMasked = mask

    ' Add the new collection variable.
    ReDim Preserve collectionVariables (UBound (collectionVariables)+1)
    Set collectionVariables(UBound(collectionVariables)) = collectionVariable

    collectionSettings.CollectionVariables=collectionVariables

    collectionSettings.Put_

 End Sub
```

```c
public void CreateCollectionVariable(
    WqlConnectionManager connection,
    string name,
    string value,
    bool mask,
    string collectionId,
    int precedence)
{
    try
    {
        IResultObject collectionSettings = null;

        // Get the collection settings. Create it if necessary.

         IResultObject collectionSettingsQuery = connection.QueryProcessor.ExecuteQuery(
                    "Select * from SMS_CollectionSettings where CollectionID='" + collectionId + "'");

         foreach (IResultObject setting in collectionSettingsQuery)
         {
             collectionSettings = setting;
         }

        if ( collectionSettings == null)
         {
             collectionSettings = connection.CreateInstance("SMS_CollectionSettings");
             collectionSettings["CollectionID"].StringValue = collectionId;
             collectionSettings.Put();
             collectionSettings.Get();
         }

        // Create the collection variable.
        List<IResultObject> collectionVariables = collectionSettings.GetArrayItems("CollectionVariables");
        IResultObject collectionVariable = connection.CreateEmbeddedObjectInstance("SMS_CollectionVariable");
        collectionVariable["Name"].StringValue = name;
        collectionVariable["Value"].StringValue = value;
        collectionVariable["IsMasked"].BooleanValue = mask;

        // Add the collection variable to the collection settings.
        collectionVariables.Add(collectionVariable);
        collectionSettings.SetArrayItems("CollectionVariables", collectionVariables);

        // Set the collection variable precedence.
        collectionSettings["CollectionVariablePrecedence"].IntegerValue = precedence;

        collectionSettings.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create collection variable: " + e.Message);
        throw;
   }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `Name` | - Managed: `String`- VBScript: `String` | The name of the variable to be created. |
| `Value` | - Managed: `String`- VBScript: `String` | The value of the variable |
| `Mask` | - Managed: `Boolean`- VBScript: `Boolean` | Specifies whether the value is displayed in the Configuration Manager console.`true` - the variable value is not displayed.`false` - the variable value is displayed. |
| `CollectionID` | - Managed: `String`- VBScript: `String` | The collection that the variable is added to. |
| `Precedence` | - Managed: `Integer`- VBScript: `Integer` | The precedence of the variable over other variables in the array. |

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