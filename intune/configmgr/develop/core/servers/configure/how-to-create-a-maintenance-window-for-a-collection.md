---
layout: Conceptual
title: Create a Maintenance Window for a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-maintenance-window-for-a-collection
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
description: Your application can create a Configuration Manager maintenance window by using the SMS_CollectionSettings Server WMI Class and SMS_ServiceWindow Server WMI Classes and properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 81e260f8-e4aa-1cda-d8c0-52a4b352ac24
document_version_independent_id: febc890e-5f6b-e6f9-0a7e-130cdda254c2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-maintenance-window-for-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-maintenance-window-for-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-maintenance-window-for-a-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: baa841d1-8bbd-9aa3-ca41-0d5690b39804
---

# Create a Maintenance Window for a Collection - Configuration Manager | Microsoft Learn

Your application can create a Configuration Manager maintenance window by using the [SMS_CollectionSettings Server WMI Class](../../../reference/core/clients/collections/sms_collectionsettings-server-wmi-class) and [SMS_ServiceWindow Server WMI Class](../../../reference/core/servers/configure/sms_servicewindow-server-wmi-class) classes and properties.

### To create a maintenance window

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the existing collection settings instance by using the supplied collection ID.
3. Create and populate the properties of a new service window object by using the [SMS_ServiceWindow Server WMI Class](../../../reference/core/servers/configure/sms_servicewindow-server-wmi-class) class.
4. Add the new `SMS_ServiceWindow` object to the collection settings instance obtained earlier.
5. Save the collection settings instance and properties.

Note

The example below includes additional steps, primarily to handle the overhead of dealing with the maintenance window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method creates a maintenance window for a collection, assuming that the collection instance can modified. This might not be the case at child sites, where the collections are owned by the parent site(s).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub CreateMaintenanceWindow(connection,                                 _
                            targetCollectionID,                         _
                            newMaintenanceWindowName,                   _
                            newMaintenanceWindowDescription,            _
                            newMaintenanceWindowServiceWindowSchedules, _
                            newMaintenanceWindowIsEnabled,              _
                            newMaintenanceWindowServiceWindowType)

    ' Build a query to get the specified collection.
     collectionSettingsQuery = "SMS_CollectionSettings.CollectionID='" & targetCollectionID & "'"

    ' Get the collection settings instance for the targetCollectionID.
    Set allCollectionSettings = connection.ExecQuery("Select * From SMS_CollectionSettings Where CollectionID = '" & targetCollectionID & "'")

    ' If a collection settings instance does not exist for the target collection, create one.
    If allCollectionSettings.Count = 0 Then
        Wscript.Echo "Creating collection settings instance."
        Set collectionSettingsInstance = connection.Get("SMS_CollectionSettings").SpawnInstance_
        collectionSettingsInstance.CollectionID = targetCollectionID
        collectionSettingsInstance.Put_
    End If

    ' Get the specific collection settings instance.
    Set collectionSettingsInstance = connection.Get("SMS_CollectionSettings.CollectionID='" & targetCollectionID &"'" )

    ' Create and populate a temporary SMS_ServiceWindow object with the new maintenance window values.
    Set tempServiceWindowObject = connection.Get("SMS_ServiceWindow").SpawnInstance_

    ' Populate temporary SMS_ServiceWindow object with the new maintenance window values.
    tempServiceWindowObject.Name = newMaintenanceWindowName
    tempServiceWindowObject.Description = newMaintenanceWindowDescription
    tempServiceWindowObject.ServiceWindowSchedules = newMaintenanceWindowServiceWindowSchedules
    tempServiceWindowObject.IsEnabled = newMaintenanceWindowIsEnabled
    tempServiceWindowObject.ServiceWindowType = newMaintenanceWindowServiceWindowType

    ' Populate the local array list with the existing service window objects (from the target collection).
    tempServiceWindowArray = collectionSettingsInstance.ServiceWindows

    ' Add the newly created service window object to the temporary array.
    ReDim Preserve tempServiceWindowArray (Ubound(tempServiceWindowArray) + 1)
    Set tempServiceWindowArray(Ubound(tempServiceWindowArray)) = tempServiceWindowObject

    ' Replace the existing service window objects from the target collection with the temporary array that includes the new service window.
    collectionSettingsInstance.ServiceWindows = tempServiceWindowArray

    ' Save the collection settings instance with the new service window object.
    collectionSettingsInstance.Put_

    ' Output success message.
    wscript.echo "New Maintenance Window created."

End Sub

```

```c

public void CreateMaintenanceWindow(WqlConnectionManager connection,
                                    string targetCollectionID,
                                    string newMaintenanceWindowName,
                                    string newMaintenanceWindowDescription,
                                    string newMaintenanceWindowServiceWindowSchedules,
                                    bool newMaintenanceWindowIsEnabled,
                                    int newMaintenanceWindowServiceWindowType)
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

        // If a collection settings instance does not exist for the target collection, create one.
        if (collectionSettingsInstance == null)
        {
            collectionSettingsInstance = connection.CreateInstance("SMS_CollectionSettings");
            collectionSettingsInstance["CollectionID"].StringValue = targetCollectionID;
            collectionSettingsInstance.Put();
            collectionSettingsInstance.Get();
        }

        // Create a new array list to hold the service window object.
        List<IResultObject> tempServiceWindowArray = new List<IResultObject>();

        // Create and populate a temporary SMS_ServiceWindow object with the new maintenance window values.
        IResultObject tempServiceWindowObject = connection.CreateEmbeddedObjectInstance("SMS_ServiceWindow");

        // Populate temporary SMS_ServiceWindow object with the new maintenance window values.
        tempServiceWindowObject["Name"].StringValue = newMaintenanceWindowName;
        tempServiceWindowObject["Description"].StringValue = newMaintenanceWindowDescription;
        tempServiceWindowObject["ServiceWindowSchedules"].StringValue = newMaintenanceWindowServiceWindowSchedules;
        tempServiceWindowObject["IsEnabled"].BooleanValue = newMaintenanceWindowIsEnabled;
        tempServiceWindowObject["ServiceWindowType"].IntegerValue = newMaintenanceWindowServiceWindowType;

        // Populate the local array list with the existing service window objects (from the target collection).
        tempServiceWindowArray = collectionSettingsInstance.GetArrayItems("ServiceWindows");

        // Add the newly created service window object to the local array list.
        tempServiceWindowArray.Add(tempServiceWindowObject);

        // Replace the existing service window objects from the target collection with the temporary array that includes the new service window.
        collectionSettingsInstance.SetArrayItems("ServiceWindows", tempServiceWindowArray);

        // Save the new values in the collection settings instance associated with the target collection.
        collectionSettingsInstance.Put();
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
| `newMaintenanceWindowName` | - Managed: `String`- VBScript: `String` | The name of the new maintenance window. |
| `newMaintenanceWindowDescription` | - Managed: `String`- VBScript: `String` | The description of the new maintenance window. |
| `newMaintenanceWindowServiceWindowSchedules` | - Managed: `String`- VBScript: `String` | The service schedules for the new maintenance window. |
| `newMaintenanceWindowIsEnabled` | - Managed: `Boolean`- VBScript: `Boolean` | `true` if the new maintenance window is enabled. |
| `newMaintenanceWindowServiceWindowType` | - Managed: `Integer`- VBScript: `Integer` | Type for the new maintenance window. |

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