---
layout: Conceptual
title: Call a WMI Class Method by Using System.Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management
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
description: To call a client Windows Management Instrumentation (WMI) class method, call the InvokeMethod of the WMI class's ManagementClass.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9b2b69ec-810f-8346-ad1b-910afe45ee0d
document_version_independent_id: 1ccceedf-7138-549d-7daa-82e48282cff2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 05f71730-b464-213b-3bc3-0502e76fc299
---

# Call a WMI Class Method by Using System.Management - Configuration Manager | Microsoft Learn

To call a client Windows Management Instrumentation (WMI) class method, in Configuration Manager, you call the `InvokeMethod` of the WMI class's `ManagementClass`.

### To call a WMI class method

1. Set up a connection to the Configuration Manager client WMI namespace. For more information, see [How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](how-to-connect-to-the-client-wmi-namespace).
2. Create a `ManagementClass` by using the `ManagementScope` path you obtain in step one, and also the name of the class you want to call a method on.
3. Create a `ManagementBaseObject` and specify any in parameters for the method.
4. Call the method by using the `ManagementClass` object `InvokeMethod` method.
5. Using the returned `ManagementBaseObject`, view the returned parameters.

## Example

The following C# code example calls the `ISmsClient::GetAssignedSite` method to get the current assigned site for the client. It then sets the assigned site back to the same value using the `ISmsClient::SetAssignedSite` method.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](how-to-call-a-wmi-class-method-by-using-system.management).

```c

public void CallMethod(ManagementScope scope)  
{  
    try// Get the client's SMS_Client class.  
    {  
        ManagementClass cls = new ManagementClass(scope.Path.Path, "sms_client", null);  

        // Get current site code.  
        ManagementBaseObject outSiteParams = cls.InvokeMethod("GetAssignedSite", null, null);  

        // Display current site code.  
        Console.WriteLine(outSiteParams["sSiteCode"].ToString());  

        // Set up current site code as input parameter for SetAssignedSite.  
        ManagementBaseObject inParams = cls.GetMethodParameters("SetAssignedSite");  
        inParams["sSiteCode"] = outSiteParams["sSiteCode"].ToString();  

        // Assign the Site code.  
        ManagementBaseObject outMPParams = cls.InvokeMethod("SetAssignedSite", inParams, null);  
    }  
    catch (ManagementException e)  
    {  
        throw new Exception("Failed to execute method", e);  
    }  
}  

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `scope` | - `ManagementScope` | A valid connection to the client WMI provider. The path is root\ccm. |

## Compiling the Code

### Namespaces

System

System.Management

### Assembly

System.Management

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](/en-us/dotnet/api/system.management.managementexception).