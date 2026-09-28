---
layout: Conceptual
title: Perform a Synchronous Query by Using System.Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management
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
description: Learn how to run a synchronous query in Configuration Manager using ManagementObjectSearcher object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c68b67a1-0fab-6964-1b57-81f32677e461
document_version_independent_id: b8fa8bc4-21c3-996f-99f1-34ab667b1ad8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3eef1dd3-7258-21d0-09a9-1d314fbb5fc8
---

# Perform a Synchronous Query by Using System.Management - Configuration Manager | Microsoft Learn

To synchronously query the Configuration Manager client Windows Management Instrumentation (WMI), you use a `ManagementObjectSearcher` object.

To read a lazy property from a Configuration Manager object that is returned in a query, you get the object instance, which in turn retrieves any lazy object properties from the SMS Provider.

### To perform a synchronous query

1. Set up a connection to the Configuration Manager client WMI namespace. For more information, see [How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](how-to-connect-to-the-client-wmi-namespace).
2. Create a ManagementObjectSearcher collection, and specify a WQL query.
3. Iterate through the ManagementObjectSearcher collection to view the ManagementObject for each WMI object that is returned by the query.

## Example

The following C# code example queries for the single `SMS_Client` object that is on a Configuration Manager client.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](how-to-call-a-wmi-class-method-by-using-system.management).

```c

public void QueryObjects(ManagementScope scope)  
{  
    try  
    {  
        ManagementObjectSearcher s = new ManagementObjectSearcher  
            ((scope), new WqlObjectQuery("SELECT * FROM sms_client"));  

        foreach (ManagementObject o in s.Get())  
        {  
            // There is only one instance of SMS_Client, so this should enumerate only once.  
            Console.WriteLine("Client version: " + o["ClientVersion"].ToString());  
        }  
    }  
    catch (System.Management.ManagementException e)  
    {  
        Console.WriteLine("Failed to make query: ", e.Message);  
        throw;  
    }  
}  
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `scope` | `ManagementScope` | Represents a scope (namespace) for management operations. |

## Compiling the Code

### Namespaces

System.

System.Management.

### Assembly

System.Management.

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](/en-us/dotnet/api/system.management.managementexception).