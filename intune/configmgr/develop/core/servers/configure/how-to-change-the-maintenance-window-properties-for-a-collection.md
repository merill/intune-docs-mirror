---
layout: Conceptual
title: Change Maintenance Window Properties for a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-change-the-maintenance-window-properties-for-a-collection
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
description: Learn how to use the Configuration Manager to change the maintenance window properties for a collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 5696a3d6-b029-f816-f59c-6cd252f73411
document_version_independent_id: a37df0fc-99ab-b863-6dcc-b4218e91e067
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-change-the-maintenance-window-properties-for-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-change-the-maintenance-window-properties-for-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-change-the-maintenance-window-properties-for-a-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 60117478-6ce7-f64e-269e-3c315a4570c6
---

# Change Maintenance Window Properties for a Collection - Configuration Manager | Microsoft Learn

You can change maintenance window properties for a collection, in Configuration Manager, by using the [SMS_CollectionSettings Server WMI Class](../../../reference/core/clients/collections/sms_collectionsettings-server-wmi-class) and [SMS_ServiceWindow Server WMI Class](../../../reference/core/servers/configure/sms_servicewindow-server-wmi-class) classes and properties.

### To change the properties of a maintenance window

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the existing collection settings instance by using the existing collection ID provided.
3. Get the existing service window object by using the existing service window ID provided.
4. Change an existing property value (in this case the maintenance window description).
5. Save the collection settings instance and properties.

Note

The steps in the example method include additional steps, primarily to handle the overhead of dealing with the service window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method changes the properties of a specific maintenance window instance.

Important

This assumes that the collection instance can modified. This might not be the case at child sites, where the collections are owned by the parent site(s).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ChangeMaintenanceWindowProperties(connection,                                 _
                                      targetCollectionID,                         _
                                      targetServiceWindowID,                            _
                                      newMaintenanceWindowDescription,            _
                                      newMaintenanceWindowServiceWindowSchedules, _
                                      newMaintenanceWindowIsEnabled)

    ' Get the specific collection settings instance.
    Set collectionSettingsInstance = connection.Get("SMS_CollectionSettings.CollectionID='" & targetCollectionID &"'" )

    ' Populate the local array list with the existing service window objects (from the target collection).
    tempMaintenanceWindowArray = collectionSettingsInstance.ServiceWindows

    ' Enumerate through the array list to access each maintenance window object.
    For Each maintenanceWindow in tempMaintenanceWindowArray

         ' If the service window ID matches the one passed in to the function, change the specific values.
         If maintenanceWindow.ServiceWindowID = targetServiceWindowID Then

            ' Populate retrieved SMS_ServiceWindow object with the new maintenance window values.
            maintenanceWindow.Description = newMaintenanceWindowDescription
            maintenanceWindow.ServiceWindowSchedules = newMaintenanceWindowServiceWindowSchedules
            maintenanceWindow.IsEnabled = newMaintenanceWindowIsEnabled

         End If

    Next

    ' Replace the existing service window objects from the target collection with the temporary array that includes the modified service window.
    collectionSettingsInstance.ServiceWindows = tempMaintenanceWindowArray

    ' Save the new values in the collection settings instance associated with the collection ID.
    collectionSettingsInstance.Put_

    ' Output success message.
    wscript.echo "Maintenance Window " & targetServiceWindowID & " modified."

End Sub

```

```c

public void ChangeMaintenanceWindowProperties(WqlConnectionManager connection,
                                              string targetCollectionID,
                                              string serviceWindowID,
                                              string newMaintenanceWindowDescription)
{
    try
    {
        // Create a new array list to hold the service window objects.
        List<IResultObject> tempMaintenanceWindowArray = new List<IResultObject>();

        // Establish connection to collection settings instance associated with the Collection ID.
        IResultObject collectionSettings = connection.GetInstance(@"SMS_CollectionSettings.CollectionID='" + targetCollectionID + "'");

        // Populate the array list with the existing service window objects (from the target collection).
        tempMaintenanceWindowArray = collectionSettings.GetArrayItems("ServiceWindows");

        // Enumerate through the array list to access each maintenance window object.
        foreach (IResultObject maintenanceWindow in tempMaintenanceWindowArray)
        {
            // If the service window ID matches the one passed in to the function, change the specific values.
            if (maintenanceWindow["ServiceWindowID"].StringValue == serviceWindowID)
            {
                maintenanceWindow["Description"].StringValue = newMaintenanceWindowDescription;
                break;
            }
        }

        // Replace the existing service window objects from the target collection with the temporary array that includes the new service window.
        collectionSettings.SetArrayItems("ServiceWindows", tempMaintenanceWindowArray);

        // Save the new values in the collection settings instance associated with the Collection ID.
        collectionSettings.Put();
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
| `serviceWindowID` | - Managed: `String`- VBScript: `String` | The ID of the maintenance window for which to change properties. |
| `newMaintenanceWindowDescription` | - Managed: `String`- VBScript: `String` | The description of the new maintenance window. |

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