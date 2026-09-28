---
layout: Conceptual
title: Get the Properties of a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-get-the-properties-of-a-collection
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
description: Learn how to establish a connection and get the properties of a specific collection instance in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 83ae60d7-fb6f-ecb6-9c3c-0d3522712534
document_version_independent_id: 47edb676-b4d3-5bf8-6bc7-803825ba6d09
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/collections/how-to-get-the-properties-of-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/collections/how-to-get-the-properties-of-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/collections/how-to-get-the-properties-of-a-collection.md
cmProducts: []
platformId: 3d798561-38da-ee58-d7d7-9cfc78f87eff
---

# Get the Properties of a Collection - Configuration Manager | Microsoft Learn

### To get the properties of a collection

1. Set up a connection to the SMS Provider.
2. Get the specific collection instance by using the collection ID provided.
3. Get the collection properties.

## Example

The following example method gets the properties of a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub ReadCollectionProperties(connection, collectionID)    Dim collection    Dim statusText    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    WScript.Echo "Processing Collection - " & CStr(collection.CollectionID)    WScript.Echo "-- Name: " & collection.Name    WScript.Echo "-- Comment: " & collection.Comment    WScript.Echo "-- Members: " & CStr(collection.MemberCount)    statusText = "None"    Select Case collection.CurrentStatus    Case 1        statusText = "Ready"    Case 2        statusText = "Refreshing"    Case 5        statusText = "Awaiting Refresh"    End Select        WScript.Echo "-- Status: " & statusTextEnd Sub  
```

```c
public void ReadCollectionProperties(WqlConnectionManager connection, string collectionID){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    string statusText = "None";    Console.WriteLine("Processing Collection - " + collectionID);    Console.WriteLine("-- Name: " + collection["Name"].StringValue);    Console.WriteLine("-- Comment: " + collection["Comment"].StringValue);    Console.WriteLine("-- Members: " + collection["MemberCount"].IntegerValue.ToString());    switch (collection["CurrentStatus"].IntegerValue)    {        case 1:            statusText = "Ready";            break;        case 2:            statusText = "Refreshing";            break;        case 5:            statusText = "Awaiting Refresh";            break;        default:            break;    }    Console.WriteLine("-- Status: " + statusText);}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `collectionID` | - Managed: `String`- VBScript: `String` | Unique auto-generated ID containing eight characters. For more information, see the CollectionID property of [SMS_Collection Server WMI Class](../../../reference/core/clients/collections/sms_collection-server-wmi-class). |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).