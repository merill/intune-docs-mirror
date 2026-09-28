---
layout: Conceptual
title: Enumerate Updates Matching a Specific Criteria - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria
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
description: Enumerate software updates that match specific criteria in Configuration Manager by building a query and then using the ExecuteQuery method of the QueryProcessor class to run the query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 340601c8-fa75-f9f6-250b-88b82d27c552
document_version_independent_id: 6e42d559-fcef-6c8f-b04d-c9f06ed1cf0e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-enumerate-updates-matching-a-specific-criteria.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: a28b9e90-647c-a829-43a2-caaeb15f62ee
---

# Enumerate Updates Matching a Specific Criteria - Configuration Manager | Microsoft Learn

This topic explains how to enumerate software updates that match specific criteria in Configuration Manager by building a query and then using the `ExecuteQuery` method of the `QueryProcessor` class to run the query.

### To enumerate updates matching a specific criteria

1. Set up a connection to the SMS Provider.
2. Assign a specific query to a variable.
3. Pass the variable to the `ExecuteQuery` method.

## Example

The following example method enumerates updates that match specific criteria by passing a query to the `ExecuteQuery` method.

Four example queries are demonstrated below:

1. A query that displays the software updates that have already been downloaded.
2. A query that displays the software updates that have already been deployed.
3. A query that displays the software updates that have a particular severity value.
4. A query that displays the software update CI\_IDs that are associated with a specific knowledge base article.

    Detailed information about the properties that are associated with a software update is in the [SMS_SoftwareUpdate](../reference/sum/sms_softwareupdate-server-wmi-class) class reference material.

    For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub EnumerateUpdatesMatchingCriteria(connection)

    ' This query displays all updates that have already been downloaded.
    Query1 = "Select * from SMS_SoftwareUpdate where IsContentProvisioned=1"

    ' Run query.
    Set ListOfResources1 = connection.ExecQuery(Query1, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection that needs to be enumerated.
    Wscript.Echo " "
    Wscript.Echo "Update Content Is Downloaded."
    Wscript.Echo "Query: " & Query1
    Wscript.Echo "--------------------------------------------------------"

    For Each Resource1 In ListOfResources1
        Wscript.Echo "Name:       " & Resource1.LocalizedDisplayName
        Wscript.Echo "ArticleID:  " & Resource1.ArticleID
        Wscript.Echo "CI_ID:      " & Resource1.CI_ID
        Wscript.Echo "Severity:   " & Resource1.SeverityName
    Next

    ' This query displays the updates that have already been deployed.
    Query2 = "Select * from SMS_SoftwareUpdate where IsDeployed=1"

    ' Run query.
    Set ListOfResources2 = connection.ExecQuery(Query2, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection that needs to be enumerated.
    Wscript.Echo " "
    Wscript.Echo "Updates Have Already Been Deployed."
    Wscript.Echo "Query: " & Query2
    Wscript.Echo "--------------------------------------------------------"

    For Each Resource2 In ListOfResources2
        Wscript.Echo "Name:       " & Resource2.LocalizedDisplayName
        Wscript.Echo "ArticleID:  " & Resource2.ArticleID
        Wscript.Echo "CI_ID:      " & Resource2.CI_ID
        Wscript.Echo "Severity:   " & Resource2.SeverityName
    Next

    ' This query displays the updates that have a particular severity value.
    Query3 = "Select * from SMS_SoftwareUpdate where SeverityName='Critical'"

    ' Run query.
    Set ListOfResources3 = connection.ExecQuery(Query3, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection that needs to be enumerated.
    Wscript.Echo " "
    Wscript.Echo "Updates That Have A Particular Severity Title."
    Wscript.Echo "Query: " & Query3
    Wscript.Echo "--------------------------------------------------------"

    For Each Resource3 In ListOfResources3
        Wscript.Echo "Name:       " & Resource3.LocalizedDisplayName
        Wscript.Echo "ArticleID:  " & Resource3.ArticleID
        Wscript.Echo "CI_ID:      " & Resource3.CI_ID
        Wscript.Echo "Severity:   " & Resource3.SeverityName
    Next

       ' This query displays software updates associated with a specific knowledge base artile.
    Query4 = "SELECT * FROM SMS_SoftwareUpdate WHERE ArticleID='832880'"

    ' Run query.
    Set ListOfResources4 = connection.ExecQuery(Query4, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' The query returns a collection that needs to be enumerated.
    Wscript.Echo " "
    Wscript.Echo "Updates For A Specific KB Article."
    Wscript.Echo "Query: " & Query4
    Wscript.Echo "--------------------------------------------------------"

    For Each Resource4 In ListOfResources4
        Wscript.Echo "Name:       " & Resource4.LocalizedDisplayName
        Wscript.Echo "ArticleID:  " & Resource4.ArticleID
        Wscript.Echo "CI_ID:      " & Resource4.CI_ID
        Wscript.Echo "Severity:   " & Resource4.SeverityName
    Next

End Sub

```

```c

public void EnumerateUpdatesMatchingCriteria(WqlConnectionManager connection)
{

    //  Note:  Query strings or variables could easily be passed in to complete the strings, but the query string
    //         must be contructed and variables resolved prior to passing the string to the ExecuteQuery method.

    try
    {

        // This query displays all updates that have already been downloaded.
        string query1 = "Select * from SMS_SoftwareUpdate where IsContentProvisioned=1";

        // Run query.
        IResultObject listOfResources1 = connection.QueryProcessor.ExecuteQuery(query1);

        // The query returns a collection that needs to be enumerated.
        Console.WriteLine(" ");
        Console.WriteLine("Update Content Is Downloaded.");
        Console.WriteLine("Query: " + query1);
        Console.WriteLine("--------------------------------------------------------");
        foreach (IResultObject resource1 in listOfResources1)
        {
            Console.WriteLine();
            Console.WriteLine("Name:       " + resource1["LocalizedDisplayName"].StringValue);
            Console.WriteLine("Article ID: " + resource1["ArticleID"].StringValue);
            Console.WriteLine("CI_ID:      " + resource1["CI_ID"].IntegerValue);
            Console.WriteLine("Severity    " + resource1["SeverityName"].StringValue);
        }

        // This query displays the updates that have already been deployed.
        string query2 = "Select * from SMS_SoftwareUpdate where IsDeployed=1";

        // Run query.
        IResultObject listOfResources2 = connection.QueryProcessor.ExecuteQuery(query2);

        // The query returns a collection that needs to be enumerated.
        Console.WriteLine(" ");
        Console.WriteLine("Updates Have Already Been Deployed.");
        Console.WriteLine("Assignments Query: " + query2);
        Console.WriteLine("--------------------------------------------------------");
        foreach (IResultObject resource2 in listOfResources2)
        {
            Console.WriteLine();
            Console.WriteLine("Name:       " + resource2["LocalizedDisplayName"].StringValue);
            Console.WriteLine("Article ID: " + resource2["ArticleID"].StringValue);
            Console.WriteLine("CI_ID:      " + resource2["CI_ID"].IntegerValue);
            Console.WriteLine("Severity:   " + resource2["SeverityName"].StringValue);
        }

        // This query displays the updates that have a particular severity value.
        string query3 = "Select * from SMS_SoftwareUpdate where SeverityName='Critical'";

        // Run query.
        IResultObject listOfResources3 = connection.QueryProcessor.ExecuteQuery(query3);

        // The query returns a collection that needs to be enumerated.
        Console.WriteLine(" ");
        Console.WriteLine("Updates That Have A Particular Severity Title.");
        Console.WriteLine("Query: " + query3);
        Console.WriteLine("--------------------------------------------------------");
        foreach (IResultObject resource3 in listOfResources3)
        {
            Console.WriteLine();
            Console.WriteLine("Name:       " + resource3["LocalizedDisplayName"].StringValue);
            Console.WriteLine("Article ID: " + resource3["ArticleID"].StringValue);
            Console.WriteLine("CI_ID:      " + resource3["CI_ID"].IntegerValue);
            Console.WriteLine("Severity:   " + resource3["SeverityName"].StringValue);
        }

        // This query displays software updates associated with a specific KB.
        string query4 = "SELECT * FROM SMS_SoftwareUpdate WHERE ArticleID='832880'";

        // Run query.
        IResultObject listOfResources4 = connection.QueryProcessor.ExecuteQuery(query4);

        // The query returns a collection that needs to be enumerated.
        Console.WriteLine(" ");
        Console.WriteLine("Updates For A Specific KB Article.");
        Console.WriteLine("Query: " + query4);
        Console.WriteLine("--------------------------------------------------------");
        foreach (IResultObject resource4 in listOfResources4)
        {
            Console.WriteLine();
            Console.WriteLine("Name:       " + resource4["LocalizedDisplayName"].StringValue);
            Console.WriteLine("Article ID: " + resource4["ArticleID"].StringValue);
            Console.WriteLine("CI_ID:      " + resource4["CI_ID"].IntegerValue);
            Console.WriteLine("Severity:   " + resource4["SeverityName"].StringValue);
        }
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to run queries. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).