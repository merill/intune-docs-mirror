---
layout: Conceptual
title: Run a Query - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-run-a-query
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
description: Run an SMS_Query based query by getting the query instance and then by running WQL query in the SMS_Query object Expression property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8e0b0c80-7928-d0d3-ed1f-b3b47571d17f
document_version_independent_id: fb75d3bb-1d2f-4547-78ed-cfb1663c248c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-run-a-query.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-run-a-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-run-a-query.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 9586e38d-a57c-1f40-6788-9b1f493076d7
---

# Run a Query - Configuration Manager | Microsoft Learn

In Configuration Manager, you run a `SMS_Query` based query by getting the query instance and then by running WQL query in the `SMS_Query` object `Expression` property.

After you have the WQL query, you can run the query either synchronously or asynchronously. The following example is synchronous. For information about running the query asynchronously, see [How to Perform an Asynchronous Configuration Manager Query by Using Managed Code](how-to-perform-an-asynchronous-query-by-using-managed-code) and [How to Perform an Asynchronous Configuration Manager Query by Using WMI](how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi). In these examples, change the `select * from collection` string to the `Expression` property value.

### To run a query

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Get the `SMS_Query` object for the query you want to run.
3. Run the query identified by the `SMS_Query` object `Expression` property.

## Example

The following example method synchronously runs the query identified by the `queryId` parameter.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub RunQuery(connection, queryId)
    Dim query
    Dim queryResults
    Dim queryResult

    ' Get query.
    Set query=connection.Get("SMS_Query.QueryID='" & queryId  & "'" )

    If err.number<>0 Then
        WScript.echo "Couldn't get Queries"
        Exit Sub
    End If

    ' Run query.
    WScript.echo query.Name
    WScript.echo "----------------------------------"

    Set queryResults=connection.ExecQuery(query.Expression)
    For Each queryResult In queryResults
        wscript.echo "     " & queryResult.Name
    Next
    If queryResults.Count=0 Then
        WScript.echo "      no query results"
    End If
End Sub
```

```c
public void RunQuery(WqlConnectionManager connection, string queryId)
{
    try
    {
        // Get the query.
        IResultObject query = connection.GetInstance(@"SMS_Query.QueryID='" + queryId + "'");

        Console.WriteLine(query["Name"].StringValue);
        Console.WriteLine("----------------------------------");

        // Get the query results.
        IResultObject queryResults = connection.QueryProcessor.ExecuteQuery(query["Expression"].StringValue);

        bool resultsFound = false;
        foreach (IResultObject queryResult in queryResults)
        {
            resultsFound = true;
            Console.WriteLine(queryResult["Name"].StringValue);
        }
        if (resultsFound == false)
        {
            Console.WriteLine("     No query results");
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to run query: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `queryID` | - Managed: `String`- VBScript: `String` | A query identifier. For more information see the `SMS_Query` class `QueryID` property. |

## Compiling the Code

The C# example has the following compilation requirements:

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

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../servers/configure/role-based-administration).