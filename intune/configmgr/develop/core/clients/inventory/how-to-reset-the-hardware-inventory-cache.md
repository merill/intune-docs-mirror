---
layout: Conceptual
title: Reset the Hardware Inventory Cache - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/how-to-reset-the-hardware-inventory-cache
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
description: In Configuration Manager, you reset the hardware inventory cache by connecting to the inventory agent namespace and deleting the inventory action status instance for hardware inventory.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0853fc9b-c76c-1329-9f54-049bca0019d5
document_version_independent_id: 3f03b9b0-f892-86c7-1dd1-4101ed330b71
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/inventory/how-to-reset-the-hardware-inventory-cache.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/inventory/how-to-reset-the-hardware-inventory-cache
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/inventory/how-to-reset-the-hardware-inventory-cache.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: bc3fbe56-ba31-ce43-e5a9-0b271795167a
---

# Reset the Hardware Inventory Cache - Configuration Manager | Microsoft Learn

In Configuration Manager, you reset the hardware inventory cache by connecting to the inventory agent namespace and deleting the inventory action status instance for hardware inventory.

### To reset the hardware inventory cache

1. Connect to the inventory agent namespace (root\ccm\invagt).
2. Delete the inventory action status instance for hardware inventory ({00000000-0000-0000-0000-000000000001}).

## Example

The following example method shows how to reset the hardware inventory cache by connecting to the inventory agent namespace and deleting the inventory action status instance for hardware inventory.

For information about calling the sample code, see [How to Call a Configuration Manager Object Class Method by Using WMI](../../understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi)

```vbs

Sub ResetHardwareInventoryCache()  

     ' Get a connection to the "root\ccm\invagt" namespace.  
    Dim locator  
    Set locator = CreateObject("WbemScripting.SWbemLocator")  
    Dim services  
    Set services = locator.ConnectServer( , "root\ccm\invagt")     

    ' Delete the specified InventoryActionStatus instance.  
    services.Delete "InventoryActionStatus.InventoryActionID='{00000000-0000-0000-0000-000000000001}'"        

    ' Display message.  
    wscript.echo "Reset Hardware Inventory cache."  

End Sub  

```

```c

// How to Reset the Hardware Inventory Cache  
public void ResetHardwareInventoryCache()  
{  
    try  
    {  
        // Define the scope (namespace).  
        ManagementScope inventoryAgentScope = new ManagementScope(@"root\ccm\invagt");  

        // Load the class that you want to work with.  
        ManagementClass inventoryClass = new ManagementClass(inventoryAgentScope.Path.Path, "InventoryActionStatus", null);  

        // Query the class for the InventoryActionID object (create query, create searcher object, execute query).  
        ObjectQuery query = new ObjectQuery("SELECT * FROM InventoryActionStatus WHERE InventoryActionID = '{00000000-0000-0000-0000-000000000001}'");  
        ManagementObjectSearcher searcher = new ManagementObjectSearcher(inventoryAgentScope, query);  
        ManagementObjectCollection queryResults = searcher.Get();  

        // Enumerate the collection to get to the result (there should only be one item returned from the query).  
        foreach (ManagementObject result in queryResults)  
        {  
            // Display message and delete the object.  
            Console.WriteLine("Resetting Hardware Inventory cache.");  
            result.Delete();  
        }  
    }  

    catch (System.Management.ManagementException ex)  
    {  
        Console.WriteLine("Failed to run action. Error: " + ex.Message);  
        throw;  
    }  
}  

```

## Compiling the Code

This C# example requires:

### Namespaces

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).