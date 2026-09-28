---
layout: Conceptual
title: Initiate a One-time Membership Evaluation for a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-initiate-a-one-time-membership-evaluation-for-a-collection
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
description: Initiate a One-time Membership Evaluation for a Collection. Get a specific collection instance by using the collection ID provided.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 567570af-5b01-035d-c912-79f6be40cda0
document_version_independent_id: dea91037-3ed6-4ad6-9ccd-a4128ac7c255
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/collections/how-to-initiate-a-one-time-membership-evaluation-for-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/collections/how-to-initiate-a-one-time-membership-evaluation-for-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/collections/how-to-initiate-a-one-time-membership-evaluation-for-a-collection.md
cmProducts: []
platformId: 52eea6e1-48e3-720f-d784-829e076fa59d
---

# Initiate a One-time Membership Evaluation for a Collection - Configuration Manager | Microsoft Learn

### To Initiate a One-time Membership Evaluation

1. Set up a connection to the SMS Provider.
2. Get the specific collection instance by using the collection ID provided.
3. Refresh the collection membership using the [RequestRefresh](../../../reference/core/clients/collections/requestrefresh-method-in-class-sms_collection) method in the [SMS_Collection](../../../reference/core/clients/collections/sms_collection-server-wmi-class) class.

## Example

The following example method refreshes the collection membership for a specific collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub RefreshCollection(connection, collectionID)    Dim collection    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    Call collection.RequestRefresh()End Sub  
```

```c
public void RefreshCollection(WqlConnectionManager connection, string collectionID){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    collection.ExecuteMethod("RequestRefresh", null);}  
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