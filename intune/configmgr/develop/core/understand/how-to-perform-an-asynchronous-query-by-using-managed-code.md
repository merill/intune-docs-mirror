---
layout: Conceptual
title: Perform an Asynchronous Query by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code
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
description: Use the ProcessQuery method to perform an asynchronous query by using the managed SMS Provider in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f582619a-be3a-e973-71e9-47ca77ecbaf0
document_version_independent_id: 69c1fe6d-c0c8-1ab9-2eb2-6441fd0e34ed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: f50a307d-8164-3632-2b53-6908f481f3d9
---

# Perform an Asynchronous Query by Using Managed Code - Configuration Manager | Microsoft Learn

In Configuration Manager, to perform an asynchronous query by using the managed SMS Provider, you use the [ProcessQuery](/en-us/previous-versions/system-center/developer/cc146295%28v=msdn.10%29) method.

The first parameter of the [ProcessQuery](/en-us/previous-versions/system-center/developer/cc146295%28v=msdn.10%29) method is an instance of the [SmsBackgroundWorker](/en-us/previous-versions/system-center/developer/cc147429%28v=msdn.10%29) class that provides two event handlers:

- [QueryProcessObjectReady](/en-us/previous-versions/system-center/developer/cc143780%28v=msdn.10%29). This event handler is called for each object returned by the query. The event handler provides an IResultObject object that represents the object.
- [QueryProcessCompleted](/en-us/previous-versions/system-center/developer/cc143778%28v=msdn.10%29). This event handler is called when the query is completed. It also provides information about any errors that occur. For more information, see For information about error handling, see [How to Handle Configuration Manager Asynchronous Errors by Using Managed Code](how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code).

    The second parameter to of the [ProcessQuery](/en-us/previous-versions/system-center/developer/cc146295%28v=msdn.10%29) method is the WQL statement for the query.

### To perform an asynchronous query

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Create the **SmsBackgroundWorker** object and populate the [QueryProcessorObjectReady](/en-us/previous-versions/system-center/developer/cc143780%28v=msdn.10%29) and [QueryProcessorCompleted](/en-us/previous-versions/system-center/developer/cc143778%28v=msdn.10%29) properties with the callback method names.
3. From the **WqlConnectionManager** object you obtain in step one, call the **QueryProcessor** object [ProcessQuery](/en-us/previous-versions/system-center/developer/cc146295%28v=msdn.10%29) method to start the asynchronous query.

## Example

The following example queries for all available SMS\_Collection objects, and in the event handler, the example writes several of the collection properties to the Configuration Manager console.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void QueryCollections(WqlConnectionManager connection)
{
    try
    {
        // Set up the query.
        SmsBackgroundWorker bw1 = new SmsBackgroundWorker();
        bw1.QueryProcessorObjectReady += new EventHandler<QueryProcessorObjectEventArgs>(bw1_QueryProcessorObjectReady);
        bw1.QueryProcessorCompleted += new EventHandler<RunWorkerCompletedEventArgs>(bw1_QueryProcessorCompleted);

        // Query for all collections.
        connection.QueryProcessor.ProcessQuery(bw1, "select * from SMS_Collection");

        // Pause while query runs.
        Console.ReadLine();
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to start asynchronous query: ", ex.Message);
    }
}

void bw1_QueryProcessorObjectReady(object sender, QueryProcessorObjectEventArgs e)
{
    try
    {
        // Get the collection.
        IResultObject collection = (IResultObject)e.ResultObject;

        //Display properties.
        Console.WriteLine(collection["CollectionID"].StringValue);
        Console.WriteLine(collection["Name"].StringValue);
        Console.WriteLine();
        collection.Dispose();
    }
    catch (SmsQueryException eX)
    {
        Console.WriteLine("Query Error: " + eX.Message);
    }
}

void bw1_QueryProcessorCompleted(object sender, RunWorkerCompletedEventArgs e)
{
    Console.WriteLine("Done...");
}
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).