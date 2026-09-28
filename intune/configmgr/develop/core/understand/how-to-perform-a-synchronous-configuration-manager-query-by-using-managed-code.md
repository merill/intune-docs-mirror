---
layout: Conceptual
title: Perform a Synchronous Query by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code
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
description: To perform a synchronous query by using the managed SMS Provider, you use *WqlConnectionManager.QueryProcessor.ExecuteQuery* method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 107c84fb-bbc6-66fe-886c-01640b1fb35c
document_version_independent_id: 2f72c957-1c54-a4d0-cbe8-71c0ce0dae3a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 6cc7cff8-aaf5-2aaf-7921-91cf4ba345a6
---

# Perform a Synchronous Query by Using Managed Code - Configuration Manager | Microsoft Learn

To perform a synchronous query by using the managed SMS Provider, you use *WqlConnectionManager.QueryProcessor.ExecuteQuery* method.

The [ExecuteQuery](/en-us/previous-versions/system-center/developer/cc146278%28v=msdn.10%29) method takes a WQL query string and optional context information for the call. An [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) is returned containing the objects found in the query.

### To perform a synchronous query

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Using the **WqlConnectionManager** object you obtain in step one, call the **QueryProcessor** object *ExecuteQuery* method to query SMS Provider and get an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) containing a collection of query results.

## Example

The following code example shows how to make a synchronous query for the available packages by using *ExecuteQuery*.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void QueryPackages(WqlConnectionManager connection)
{
    try
    {
        IResultObject query = connection.QueryProcessor.ExecuteQuery("Select * from SMS_Package");
        foreach (IResultObject o in query)
        {
            Console.WriteLine(o["Name"].StringValue);
            o.Dispose();
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to query packages: " + ex.Message);
        throw;
    }
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