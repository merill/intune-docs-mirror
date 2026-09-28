---
layout: Conceptual
title: List Maintenance Windows and Properties for a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-list-the-maintenance-windows-and-properties-for-a-specific-collection
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
description: Learn how to list the maintenance windows and properties for a specific collection with provided examples and links.
locale: en-us
document_id: fb4db91a-95b5-ed8a-7d90-8fb8b0a4d899
document_version_independent_id: ab2d017c-5beb-f4a0-4ec7-e5d242c506a8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-list-the-maintenance-windows-and-properties-for-a-specific-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-list-the-maintenance-windows-and-properties-for-a-specific-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-list-the-maintenance-windows-and-properties-for-a-specific-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ddadc2fd-f0bd-e7ca-ea6d-232aa8e7aa7a
---

# List Maintenance Windows and Properties for a Collection - Configuration Manager | Microsoft Learn

The following example shows how to list the maintenance windows for a specific collection by using the [SMS_CollectionSettings Server WMI Class](../../../reference/core/clients/collections/sms_collectionsettings-server-wmi-class) class. Maintenance windows are created by using the [SMS_ServiceWindow Server WMI Class](../../../reference/core/servers/configure/sms_servicewindow-server-wmi-class) class and then stored as embedded objects in [SMS_CollectionSettings](../../../reference/core/clients/collections/sms_collectionsettings-server-wmi-class) instances, one per collection.

### To list the maintenance windows and properties for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the existing collection settings instance by using the collection ID provided.
3. Enumerate the existing service window objects and properties.

Note

The example method includes additional steps, primarily to handle the overhead of dealing with the service window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method lists the maintenance windows and properties for a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ListMaintenanceWindowsAndPropertiesForASpecificCollection(connection,         _
                                                              targetCollectionID)

    ' Build a query to get the specified collection.
     collectionSettingsQuery = "SMS_CollectionSettings.CollectionID='" & targetCollectionID & "'"

    ' Get the collection settings instance for the targetCollectionID.
    Set allCollectionSettings = connection.ExecQuery("Select * From SMS_CollectionSettings Where CollectionID = '" & targetCollectionID & "'")

    ' If a collection settings instance does not exist, output a message.
    If allCollectionSettings.Count = 0 Then
        Wscript.Echo "There are no maintenance windows for collection: " & targetCollectionID
    Else

    ' Get the specific collection settings instance.
    Set collectionSettingsInstance = connection.Get("SMS_CollectionSettings.CollectionID='" & targetCollectionID &"'" )

        ' Populate the local array list with the existing service window objects (from the target collection).
        tempMaintenanceWindowArray = collectionSettingsInstance.ServiceWindows

        ' Enumerate through the array list to access each maintenance window object.
        For Each maintenanceWindow in tempMaintenanceWindowArray

                Wscript.Echo "Maintenance Window Properties "
                Wscript.Echo "----------------------------- "
                Wscript.Echo "Name:              " & maintenanceWindow.Name
                Wscript.Echo "Description:       " & maintenanceWindow.Description
                Wscript.Echo "Service Window ID: " & maintenanceWindow.ServiceWindowID
                Wscript.Echo "Schedules:         " & maintenanceWindow.ServiceWindowSchedules
                Wscript.Echo "Is Enabled:        " & maintenanceWindow.IsEnabled
                Wscript.Echo "Type:              " & maintenanceWindow.ServiceWindowType
                Wscript.Echo " "

        Next

    End If

End Sub

```

```c

public void ListMaintenanceWindowsAndPropertiesForASpecificCollection(WqlConnectionManager connection,
                                                                      string targetCollectionID)
{
    try
    {
        // Create an object to hold the collection settings instance (used to check whether a collection settings instance exists).
        IResultObject collectionSettingsInstance = null;

        // Get the collection settings instance for the targetCollectionID.
        IResultObject allCollectionSettings = connection.QueryProcessor.ExecuteQuery("Select * from SMS_CollectionSettings where CollectionID='" + targetCollectionID + "'");

        // Enumerate the allCollectionSettings collection (there should be just one item) and save the instance.
        foreach (IResultObject collectionSetting in allCollectionSettings)
        {
            collectionSettingsInstance = collectionSetting;
        }

        // If a collection settings instance, output message that there are no maintenance windows.
        if (collectionSettingsInstance == null)
        {
            Console.WriteLine("There are no maintenance windows for collection: " + targetCollectionID);
        }
        else
        {
            // Create a new array list to hold the service window objects.
            List<IResultObject> maintenanceWindowArray = new List<IResultObject>();

            // Establish connection to collection settings instance associated with the Collection ID.
            IResultObject collectionSettings = connection.GetInstance(@"SMS_CollectionSettings.CollectionID='" + targetCollectionID + "'");

            // Populate the array list with the existing service window objects (from the target collection).
            maintenanceWindowArray = collectionSettings.GetArrayItems("ServiceWindows");

            // Enumerate through the array list to access each maintenance window object and output specific properties for each object.
            foreach (IResultObject maintenanceWindow in maintenanceWindowArray)
            {
                Console.WriteLine("Maintenance Window Properties ");
                Console.WriteLine("----------------------------- ");
                Console.WriteLine("Name:              " + maintenanceWindow["Name"].StringValue);
                Console.WriteLine("Description:       " + maintenanceWindow["Description"].StringValue);
                Console.WriteLine("Service Window ID: " + maintenanceWindow["ServiceWindowID"].StringValue);
                Console.WriteLine("Schedules:         " + maintenanceWindow["ServiceWindowSchedules"].StringValue);
                Console.WriteLine("Is Enabled:        " + maintenanceWindow["IsEnabled"].BooleanValue);
                Console.WriteLine("Type:              " + maintenanceWindow["ServiceWindowType"].IntegerValue);
                Console.WriteLine(" ");
            };
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `targetCollectionID` | - Managed: `String`- VBScript: `String` | The ID of the collection. |

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