---
layout: Conceptual
title: Initiate a Synchronization - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization
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
description: Learn how to synchronize the asset intelligence catalog outside the normal synchronization schedule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9f5bb551-bb30-0073-6131-a86ab319b913
document_version_independent_id: d6db80a7-b066-55a9-05df-960bcff40a97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: bbe2ba8f-da15-b8f2-5c53-7a3242f267a8
---

# Initiate a Synchronization - Configuration Manager | Microsoft Learn

The Asset Intelligence catalog can be refreshed manually, outside the normal synchronization schedule. A manual refresh is accomplished by using the [RequestCatalogUpdate](../../../reference/core/clients/asset-intelligence/requestcatalogupdate-method-in-class-sms_aiproxy) method on the [SMS_AIProxy Server WMI Class](../../../reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class).

Important

This method can only be called once within a 12 hours period, subsequent method calls will not work.

### Refresh the Asset Intelligence catalog

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Query the SMS Provider for the [SMS_AIProxy](../../../reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class) instance that you want refresh the catalog on.
3. Call the SMS\_AIProxy class [RequestCatalogUpdate](../../../reference/core/clients/asset-intelligence/requestcatalogupdate-method-in-class-sms_aiproxy) method to run an action on the collection.

## Example

The following example method runs the refresh on the provided server.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Function InitiateSync(connection, serverName)
    On Error Resume Next    
    Dim classObj: Set classObj = connection.Get("SMS_AIProxy")    
    Dim inParams: Set inParams = classObj.Methods_("RequestCatalogUpdate").InParameters.SpawnInstance_()
    Dim outParams
    inParams.Properties_.Item("ProxyName") = serverName
    Set outParams = connection.ExecMethod("SMS_AIProxy", "RequestCatalogUpdate", inParams)
    If Err.Number <> 0 Then
        InitiateSync = False
    Else
        InitiateSync = True
    End If
    On Error Goto 0
End Function  
```

```c
public void InitiateSync(WqlConnectionManager connection, string serverName)
{
    try
    {        
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        IResultObject classObj = connection.GetClassObject("SMS_AIProxy");
        inParams.Add("ProxyName", serverName);
        Console.WriteLine("Requesting catalog update on server " + serverName);
        classObj.ExecuteMethod("RequestCatalogUpdate", inParams);    
    }    
    catch (SmsException ex)    
    {        
        Console.WriteLine(String.Format("Failed to request catalog update on server {0}. Error: {1}", serverName, ex.Message));           
        throw;    
    }
}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| connection | Managed: `WqlConnectionManager` VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the provider. |
| serverName | Managed: `String` VBScript: `String` | Name of the server to run the refresh on. This name maps to the `ProxyName` property of an `SMS_AIProxy` instance. |

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).