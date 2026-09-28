---
layout: Conceptual
title: Perform an Asynchronous Query by Using System.Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management
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
description: To perform an asynchronous query on a Configuration Manager client Windows Instrumentation (WMI) namespace, create a ManagementObjectSearcher object that specifies a WQL query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2971e450-1654-027b-a655-5eb50c38f67f
document_version_independent_id: aaddd6a8-eb9b-f7aa-911a-688b7668b686
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b6237e91-762b-9821-c3d2-99f23efa3dfc
---

# Perform an Asynchronous Query by Using System.Management - Configuration Manager | Microsoft Learn

To perform an asynchronous query on a Configuration Manager client Windows Instrumentation (WMI) namespace, create a `ManagementObjectSearcher` object that specifies a WQL query. You then create a `ManagementOperationObserver` that specifies an event handler for each query result and also for the end of the query.

The asynchronous query is run when the `ManagementObjectSearcher` object Get method is called with the `ManagementOperationObserver` object.

### To perform an asynchronous query

1. Set up a connection to the Configuration Manager client WMI namespace. For more information, see [How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](how-to-connect-to-the-client-wmi-namespace).
2. Create a `ManagementObjectSearcher` object.
3. Create a `ManagementOperationObserver` object.
4. Add an `ObjectReadyEventHandler` method the `ManagementOperationObserver` object.
5. Add a `CompletedEventHandler` method to the `ManagementOperationObserver`.
6. Call the `ManagementObjectSearcher` object Get method and supply the `ManagmentOperationObserver` object as a parameter.
7. Ensure your application still runs while the query is run.

## Example

The following C# code example asynchronously queries for components that are installed on a client.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](how-to-call-a-wmi-class-method-by-using-system.management).

```c

public void EnumerateInstancesAsync(ManagementScope scope)  
{  
    try  
    {  
        // Instantiate an object searcher with the query.  
        ManagementObjectSearcher searcher =  
            new ManagementObjectSearcher(scope, new  
            SelectQuery("CCM_InstalledComponent"));  

        // Create a results watcher object  
        // and handler for results and completion.  
        ManagementOperationObserver results = new  
            ManagementOperationObserver();  

        // Attach handler to events for results and completion.  
        results.ObjectReady += new  
            ObjectReadyEventHandler(this.NewObject);  
        results.Completed += new  
            CompletedEventHandler(this.Done);  

        Console.WriteLine("Installed Components");  
        Console.WriteLine("--------------------");  
        Console.WriteLine();  

        // Call the asynchronous overload of Get()  
        // to start the enumeration.  
        searcher.Get(results);  

        // Do something else while results  
        // arrive asynchronously.  
        while (!this.Completed)  
        {  
            System.Threading.Thread.Sleep(1000);  
        }  

        this.Reset();  
    }  
    catch (ManagementException e)  
    {  
        Console.WriteLine("Failed to run query: " + e.Message);  
        throw;  
    }  

}  

private bool isCompleted = false;  

private void NewObject(object sender,  
    ObjectReadyEventArgs obj)  
{  
    try  
    {  
        Console.WriteLine("Name: {0}, Version = {1}",  
            obj.NewObject["DisplayName"],  
            obj.NewObject["Version"]);  
    }  
    catch (ManagementException e)  
    {  
        Console.WriteLine("Error: " + e.Message);  
    }  

}  

private bool Completed  
{  
    get  
    {  
        return isCompleted;  
    }  
}  

private void Reset()  
{  
    isCompleted = false;  
}  

private void Done(object sender,  
         CompletedEventArgs obj)  
{  
    isCompleted = true;  
}  

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Scope` | `ManagementScope` | A valid `ManagementScope`. The path should be root\ccm. |

## Compiling the Code

### Namespaces

System.

System.Management.

### Assembly

System.Management.

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](/en-us/dotnet/api/system.management.managementexception).