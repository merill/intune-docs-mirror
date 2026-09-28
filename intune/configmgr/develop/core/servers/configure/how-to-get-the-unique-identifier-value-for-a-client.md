---
layout: Conceptual
title: Get the Unique Identifier Value for a Client - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-get-the-unique-identifier-value-for-a-client
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
description: When you discover system resource data for a client, in Configuration Manager, you must specify the client's unique identifier value in the data discovery record (DDR).
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 451f515f-8c9e-f5bf-44b6-d0dc0b825e2c
document_version_independent_id: a492686a-9c87-bcc5-3d05-5128eaacb971
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-get-the-unique-identifier-value-for-a-client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-get-the-unique-identifier-value-for-a-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-get-the-unique-identifier-value-for-a-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1f383729-1151-3c33-1262-68a98a953874
---

# Get the Unique Identifier Value for a Client - Configuration Manager | Microsoft Learn

When you discover system resource data for a client, in Configuration Manager, you must specify the client's unique identifier value in the data discovery record (DDR), such as:

```
DDRAddString("SMS Unique Identifier",
             "GUID:12345678-1234-1234-1234-123456789012", 64,
             ADDPROP_GUID | ADDPROP_KEY);
```

The client's unique identifier can be found in Windows Management Instrumentation (WMI) at:

```
root\ccm:CCM_Client=@:ClientId
```

## Procedures

#### To identify the client's unique identifier in WMI

1. Connect to the CCM namespace (root\ccm).
2. Load the `CCM_Client` class.
3. Enumerate through the objects in the `CCM_Client` class and display the unique identifier (ClientId).

## Example

### Description

The following example method shows how to obtain the client's unique identifier from WMI by connecting to the CCM namespace, loading the `CCM_Client` class and getting the ClientId property.

Important

The following C# example requires the System.Management namespace.

For information about calling the sample code, see [How to Call a Configuration Manager Object Class Method by Using WMI](../../understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi)

### Code

```vbs

Sub GetClientUniqueID()

    ' Get a connection to the root\ccm namespace on the local system.
    Set objWMIService = GetObject("winmgmts:\\.\root\ccm")

    ' Get all objects in the CCM_Client class.
    set allCCMClientObjects = objWMIService.ExecQuery("Select * from CCM_Client")

    ' Loop through the available objects (only one) and display ClientId value.
    For Each eachCCMClientObject in allCCMClientObjects
       wscript.echo "ClientId (GUID): " & eachCCMClientObject.ClientId
    Next

End Sub
```

```c

public void GetClientUniqueID()
{
    try
    {
        // Define the scope (namespace) to connect to.
        ManagementScope inventoryAgentScope = new ManagementScope(@"root\ccm");

        // Load the class to work with (CCM_Client).
        ManagementClass inventoryClass = new ManagementClass(inventoryAgentScope.Path.Path, "CCM_Client", null);

        // Query the class for the objects (create query, create searcher object, execute query).
        ObjectQuery query = new ObjectQuery("SELECT * FROM CCM_Client");
        ManagementObjectSearcher searcher = new ManagementObjectSearcher(inventoryAgentScope, query);
        ManagementObjectCollection queryResults = searcher.Get();

        // Loop through the available objects (only one) and display the ClientId value.

        foreach (ManagementObject result in queryResults)
        {
            Console.WriteLine("ClientId (GUID): " + result["ClientId"]);
        }
    }

    catch (System.Management.ManagementException ex)
    {
        Console.WriteLine("Failed to get client ID (GUID). Error: " + ex.Message);
        throw;
    }
}

```

### Comments

## Compiling the Code

This C# example requires:

#### Namespaces

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).