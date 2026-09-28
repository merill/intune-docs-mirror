---
layout: Conceptual
title: Delete a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-delete-a-collection
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
description: Learn how your application can delete a collection in Configuration Manager by using the SMS_Collection Server WMI Class and class properties.
ms.date: 2016-12-06T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 04f1bb13-1bbe-31de-4a1b-457a8f5b9e1f
document_version_independent_id: c4c6bfac-1aa8-82fc-b317-2f81e9ec1809
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/collections/how-to-delete-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/collections/how-to-delete-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/collections/how-to-delete-a-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c1bd985e-63bf-f4e8-8e34-351f1689d6b7
---

# Delete a Collection - Configuration Manager | Microsoft Learn

Your application can delete a collection in Configuration Manager by using the [SMS_Collection Server WMI Class](../../../reference/core/clients/collections/sms_collection-server-wmi-class) and class properties.

Important

- Care should be exercised when deleting any Configuration Manager object.
- We recommend that if you are deleting several collections, you do so one at a time, to allow database operations time to manage changes associated with the deletions.

Collections are closely tied to packages, programs, and advertisements. For more information, see [Software Distribution Overview](../../servers/configure/software-distribution-overview).

These examples require the following values:

- A Windows Management Instrumentation (WMI) connection object.
- An existing collection ID.

    The following code is an example of the subroutine call in Visual Basic:

```
Call DeleteCollection(swbemServices,"ABC00010")  
```

The following code is an example of the method call in C#:

```
DeleteCollection(WMIConnection,"ABC00010")  
```

### To delete a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the specific collection instance by using the collection ID provided.
3. Delete the collection by using the delete method.

## Example

The following example method deletes a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

' Setup a connection to the local provider.  
Set swbemLocator = CreateObject("WbemScripting.SWbemLocator")  
Set swbemServices= swbemLocator.ConnectServer(".", "root\sms")  
Set providerLoc = swbemServices.InstancesOf("SMS_ProviderLocation")  

For Each Location In providerLoc  
    If location.ProviderForLocalSite = True Then  
        Set swbemServices = swbemLocator.ConnectServer(Location.Machine, "root\sms\site_" + Location.SiteCode)  
        Exit For  
    End If  
Next  

Call DeleteCollection(swbemServices,"ABC00010")  

Sub DeleteCollection(connection, collectionIDToDelete)  

    ' Get the specific collection instance to delete.  
    Set collectionToDelete = connection.Get("SMS_Collection.CollectionID='" & collectionIDToDelete & "'")  

    ' Delete the collection.  
    collectionToDelete.Delete_  

    ' Display change information.  
    Wscript.Echo "Deleted collection: " & collectionIDToDelete  

End Sub  
```

```c
public void DeleteCollection(WqlConnectionManager connection, string collectionIDToDelete)  
{  
    //  Note:  On delete, the provider cleans up the SMS_CollectionSettings and SMS_CollectToSubCollect objects.  

    try  
    {  
        // Get the specific collection instance to delete.  
        IResultObject collectionToDelete = connection.GetInstance(@"SMS_Collection.CollectionID='" + collectionIDToDelete + "'");  

        // Delete the collection.  
        collectionToDelete.Delete();  

        // Output the ID of the deleted collection.  
        Console.WriteLine("Deleted collection: " + collectionIDToDelete);  
    }  

    catch (SmsException ex)  
    {  
        Console.WriteLine("Failed to delete collection. Error: " + ex.Message);  
        throw;  
    }  
}  

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `collectionIDToDelete` | - Managed: `String`- VBScript: `String` | Unique auto-generated ID containing eight characters. For more information, see the `CollectionID` property of [SMS_Collection Server WMI Class](../../../reference/core/clients/collections/sms_collection-server-wmi-class). |

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

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).