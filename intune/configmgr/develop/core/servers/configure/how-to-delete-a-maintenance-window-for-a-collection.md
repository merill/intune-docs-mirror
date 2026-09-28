---
layout: Conceptual
title: Delete a Maintenance Window for a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-delete-a-maintenance-window-for-a-collection
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
description: Learn how to delete a maintenance window for a collection in Configuration Manager with the following example.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bd6e6e13-7546-d88b-4611-7520cf5e26a5
document_version_independent_id: 9b56e7bf-4ebe-c2e4-dee3-badcf370df1b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-delete-a-maintenance-window-for-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-delete-a-maintenance-window-for-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-delete-a-maintenance-window-for-a-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 80e5626f-1689-fe98-7151-5bd9e5f3a837
---

# Delete a Maintenance Window for a Collection - Configuration Manager | Microsoft Learn

You can delete maintenance window, in Configuration Manager, by using the [SMS_CollectionSettings Server WMI Class](../../../reference/core/clients/collections/sms_collectionsettings-server-wmi-class) and [SMS_ServiceWindow Server WMI Class](../../../reference/core/servers/configure/sms_servicewindow-server-wmi-class) classes and properties.

### To delete a maintenance window for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get an existing collection settings instance by using the collection ID provided.
3. Get the existing service window object by using the maintenance window ID provided.
4. Delete the existing maintenance window.
5. Save the collection settings instance and properties.

Note

The example method includes additional steps, primarily to handle the overhead of dealing with the service window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method deletes a specific maintenance window instance for a collection.

Important

This assumes that the collection instance can modified. This might not be the case at child sites, where the collections are owned by the parent site or sites.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```c
public void DeleteMaintenanceWindowfromCollection(WqlConnectionManager connection,
                                                  string targetCollectionID,
                                                  string serviceWindowID)
{
    try
    {
        // Create a new array list to hold the service window objects.
        List<IResultObject> tempMaintenanceWindowArray = new List<IResultObject>();

        // Establish connection to collection settings instance associated with the target collection ID.
        IResultObject collectionSettings = connection.GetInstance(@"SMS_CollectionSettings.CollectionID='" + targetCollectionID + "'");

        // Populate the array list with the existing service window objects (from the target collection).
        tempMaintenanceWindowArray = collectionSettings.GetArrayItems("ServiceWindows");

        // Enumerate through the array list to access each maintenance window object.
        foreach (IResultObject maintenanceWindow in tempMaintenanceWindowArray)
        {
            // If the maintenance window ID matches the one passed in to the function, delete the maintenance window.
            if (maintenanceWindow["ServiceWindowID"].StringValue == serviceWindowID)
            {
                tempMaintenanceWindowArray.Remove(maintenanceWindow);
                Console.WriteLine("Deleted:");
                Console.WriteLine("Maintenance Window Name: " + maintenanceWindow["Name"].StringValue);
                Console.WriteLine("Maintenance Windows Service Window ID: " + maintenanceWindow["ServiceWindowID"].StringValue);
                break;
            }
        }

        // Replace the existing service window objects from the target collection with the temporary array that includes the new maintenance window.
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
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `targetCollectionID` | - Managed: `String` | The ID of the collection. |
| `serviceWindowID` | - Managed: `String` | The ID of the maintenance window to delete. |

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