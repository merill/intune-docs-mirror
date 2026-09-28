---
layout: Conceptual
title: Read a WMI Object by Using System.Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management
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
description: Learn how to use a ManagementObject object to read the Windows Management Instrumentation (WMI) object in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a6850a64-65bc-9fa9-050e-1c76922b302a
document_version_independent_id: 1522d81c-8ff2-39bf-877b-1cd17121e8c0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4077ff4a-2f31-512c-b3bb-738ae89ea37d
---

# Read a WMI Object by Using System.Management - Configuration Manager | Microsoft Learn

To read a Configuration Manager client Windows Management Instrumentation (WMI) object, in Configuration Manager, you use a `ManagementObject` object to read the WMI object.

### To read a WMI object

1. Set up a connection to the Configuration Manager client WMI namespace. For more information, see [How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](how-to-connect-to-the-client-wmi-namespace).
2. Create a `ManagementObject` object.
3. Create a `ManagementPath` object with the `ManagementScope` path you obtain from step one.
4. Assign the `ManagementPath` object to the `ManagementObject` path property.
5. Call the `ManagementObject` object Get method to get the object from the WMI provider.
6. Use the `ManagementObject` object to read the WMI provider object properties.

## Example

The following C# code example gets the Configuration Manager client WMI object [SMS_Client](../../../reference/core/clients/client-classes/sms_client-client-wmi-class) object and displays its properties.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](how-to-call-a-wmi-class-method-by-using-system.management).

```c

void ReadObject(ManagementScope scope)  
{  
    try  // Gets an instance of a CCM_InstalledComponent.  
    {  
        // Get the object.  
        ManagementObject obj = new ManagementObject();  
        ManagementPath path = new ManagementPath(scope.Path + ":CCM_InstalledComponent.Name='SMSClient'");  

        obj.Path = path;  
        obj.Get();  

        // Display a single property.  
        Console.WriteLine(obj["DisplayName"].ToString());  

        // Display all properties.  
        foreach (PropertyData property in obj.Properties)  
        {  
            Console.WriteLine(property.Name + " " + property.Value);  
        }  
    }  
    catch (ManagementException e)  
    {  
        Console.WriteLine("Failed to get component: " + e.Message);  
        throw;  
    }  
}  
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `scope` | - `ManagementScope` | The client management scope. The namespace should be root\ccm. |

## Compiling the Code

### Namespaces

System

System.Management

### Assembly

System.Management

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](/en-us/dotnet/api/system.management.managementexception).