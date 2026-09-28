---
layout: Conceptual
title: Connect to the Client WMI Namespace - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace
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
description: Learn how to connect to the Configuration Manager client Windows Management Instrumentation (WMI) provider, you create a ManagementScope object in the \\\Client\root\ccm namespace.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a17bc11b-7866-e804-5a0b-85fbccd0159d
document_version_independent_id: 7a0cbd00-bd32-ed11-1726-15c95d706abc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
platformId: a29576fe-bf9f-1686-9514-1b4aaea08cae
---

# Connect to the Client WMI Namespace - Configuration Manager | Microsoft Learn

To connect to the Configuration Manager client Windows Management Instrumentation (WMI) provider, you create a `ManagementScope` object in the \\Client\root\ccm namespace.

You use the `ManagementScope` object to read and query WMI objects. For example, [How to Read a WMI Object Using System.Management](how-to-read-a-wmi-object-by-using-system.management).

### To connect to the Configuration Manager client WMI provider

1. In Visual Studio, create a new Visual C# Console Project.
2. Add a reference to the System.Management assembly.
3. In the C# source code, add a reference to the System.Management namespace with the following code.
4. `using System.Management;`
5. Create a new class and add the following connection example code.

## Example

The following C# code example creates and returns a `ManagementScope` object on the root\ccm namespace.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](how-to-call-a-wmi-class-method-by-using-system.management).

```c

public ManagementScope Connect()  
{  
    try  
    {  
        return new ManagementScope(@"root\ccm");  
    }  
    catch (System.Management.ManagementException e)  
    {  
        Console.WriteLine("Failed to connect", e.Message);  
        throw;  
    }  
}  

```

## Compiling the Code

### Namespaces

System

System.Management

### Assembly

System.Management.dll

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](/en-us/dotnet/api/system.management.managementexception).