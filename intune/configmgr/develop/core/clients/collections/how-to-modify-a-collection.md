---
layout: Conceptual
title: Modify a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-modify-a-collection
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
description: How to modify a collection by using the collection ID provided. The example property values are modified using the name and comment values.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 05610d1b-2be1-df05-c646-c0619fac2b38
document_version_independent_id: d6d2bcc6-4695-bf63-2c44-13dc565df974
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/collections/how-to-modify-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/collections/how-to-modify-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/collections/how-to-modify-a-collection.md
cmProducts: []
platformId: 0ccc9a2a-4f78-83db-ad2b-954ed1f7e111
---

# Modify a Collection - Configuration Manager | Microsoft Learn

### To Modify a Collection

1. Set up a connection to the SMS Provider.
2. Get the specific collection instance by using the collection ID provided.
3. Display the current property values (name and comment properties used as examples).
4. Modify the example property values using the `name` and `comment` values passed in.

## Example

The following example method shows how to modify collection properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub RenameCollection(connection, collectionID, name, comment)    Dim collection    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    WScript.Echo "-- Collection " & collectionID & " --"    WScript.Echo "Name before: " & collection.Name    WScript.Echo "Comment before: " & collection.Comment    collection.Name = name    collection.Comment = comment    collection.Put_    WScript.Echo ""    WScript.Echo "Name after: " & collection.Name    WScript.Echo "Comment after: " & collection.CommentEnd Sub  
```

```c
public void RenameCollection(WqlConnectionManager connection, string collectionID, string name, string comment){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    Console.WriteLine("-- Collection {0} --", collectionID);    Console.WriteLine("Name before: {0}", collection["Name"].StringValue);    Console.WriteLine("Comment before: {0}", collection["Comment"].StringValue);    collection["Name"].StringValue = name;    collection["Comment"].StringValue = comment;    collection.Put();    collection.Get();    Console.WriteLine();    Console.WriteLine("Name after: {0}", collection["Name"].StringValue);    Console.WriteLine("Comment after: {0}", collection["Comment"].StringValue);}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| collectionID | - Managed: `String`- VBScript: `String` | Unique auto-generated ID containing eight characters. For more information, see the CollectionID property of [SMS_Collection Server WMI Class](../../../reference/core/clients/collections/sms_collection-server-wmi-class). |
| name | - Managed: `String`- VBScript: `String` | An example collection property. The property value is modified in the code snippet. |
| comment | - Managed: `String`- VBScript: `String` | An example collection property. The property value is modified in the code snippet. |

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