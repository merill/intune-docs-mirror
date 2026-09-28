---
layout: Conceptual
title: Enumerate the Members of a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-enumerate-the-members-of-a-collection
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
description: In Configuration Manager, the preferred method to enumerate through a collection is to use SMS_FullCollectionMembership Server WMI Class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e1a79631-4313-9fd5-9f9c-fd1af2e06322
document_version_independent_id: f9bc810c-9537-f0b3-d840-4e1a1304b237
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/collections/how-to-enumerate-the-members-of-a-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/collections/how-to-enumerate-the-members-of-a-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/collections/how-to-enumerate-the-members-of-a-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c81d3dc5-86ab-73ee-eab8-030d71ee2f0f
---

# Enumerate the Members of a Collection - Configuration Manager | Microsoft Learn

In Configuration Manager, the preferred method to enumerate through a collection is to use `SMS_FullCollectionMembership Server WMI Class`.

**Query 1: SMS\_FullCollectionMembership**: This example shows how to enumerate the members of the All Systems (SMS00001) collection by using the `SMS_FullCollectionMembership Server WMI Class`.

**Query 2: SMS\_CollectionMember\_a**: This example shows a slower alternative, by using the [SMS_CollectionMember_a Server WMI Class](../../../reference/core/clients/collections/sms_collectionmember_a-server-wmi-class) class.

**Query 3: SMS\_Collection**: This example shows a further alternative, which is to query the members by using the actual collection class name that is specified in the `MemberClassName` property of [SMS_Collection Server WMI Class](../../../reference/core/clients/collections/sms_collection-server-wmi-class). Querying the actual class offers performance advantages and lets you create more complex queries, such as JOINs. The example is equivalent to the earlier queries.

Note

When the SMS Provider first initializes, it registers and dynamically loads the SMS collection class into memory. If a WQL query is made against the collection class before it is loaded, an empty query result set will be returned.

Collections are closely tied to packages, programs and advertisements. For more information, see [Software Distribution Overview](../../servers/configure/software-distribution-overview).

These examples require the following values:

- A Windows Management Instrumentation (WMI) connection object.

    Example of the subroutine call in Visual Basic:

```
Call EnumerateCollectionMembers(swbemServices)  
```

Example of the method call in C#:

```
EnumerateCollectionMembers(WMIConnection)  
```

### To enumerate the members of a collection

1. Set up a connection to the SMS Provider.
2. Define a query to select the resources for the collection.
3. Execute the query and enumerate the results.

## Example

The following example method enumerates the members of a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub EnumerateCollectionMembers(connection)  
    Const wbemFlagReturnImmediately = 16    Const wbemFlagForwardOnly = 32  
    ' Set required variables.  
    ' Note:  Values must be manually added to the queries below.  
    Dim Query1    Dim Query2    Dim Query3    Dim ListOfResources1    Dim ListOfResources2    Dim ListOfResources3    Dim Resource1    Dim Resource2    Dim Resource3  
    ' The following example shows how to enumerate the members of the All Systems (SMS00001) collection.  
    Query1 = "SELECT ResourceID FROM SMS_FullCollectionMembership WHERE CollectionID = 'SMS00001'"   

    ' Run query.  
    Set ListOfResources1 = connection.ExecQuery(Query1, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)  

    ' The query returns a collection that needs to be enumerated.  
    Wscript.Echo " "  
    Wscript.Echo "Query: " & Query1  
    For Each Resource1 In ListOfResources1       
        Wscript.Echo Resource1.ResourceID     
    Next  

    ' A slower alternative is to use the SMS_CollectionMember_a association class.  
    Query2 = "SELECT ResourceID FROM SMS_CollectionMember_a WHERE CollectionID = 'SMS00001'"   

    ' Run query.  
    Set ListOfResources2 = connection.ExecQuery(Query2, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)  

    ' The query returns a collection that needs to be enumerated.  
    Wscript.Echo " "  
    Wscript.Echo "Query: " & Query2  
    For Each Resource2 In ListOfResources2       
        Wscript.Echo Resource2.ResourceID     
    Next  

    ' A further alternative is to query the members by using the actual collection class name specified in the MemberClassName property of SMS_Collection.   
    Query3 = "SELECT ResourceID FROM SMS_CM_Res_Coll_SMS00001"   

    ' Run query.  
    Set ListOfResources3 = connection.ExecQuery(Query3, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)  

    ' The query returns a collection that needs to be enumerated.  
    Wscript.Echo " "  
    Wscript.Echo "Query: " & Query3  
    For Each Resource3 In ListOfResources3       
        Wscript.Echo Resource3.ResourceID     
    Next  

End Sub  
```

```c
public void EnumerateCollectionMembers(WqlConnectionManager connection)  
{  
    // Set required variables.  
    // Note:  Values must be manually added to the queries below.  

    try  
    {  
        // The following example shows how to enumerate the members of the All Systems (SMS00001) collection.  
        string Query1 = "SELECT ResourceID FROM SMS_FullCollectionMembership WHERE CollectionID = 'SMS00001'";  

        // Run query.  
        IResultObject ListOfResources1 = connection.QueryProcessor.ExecuteQuery(Query1);  

        // The query returns a collection that needs to be enumerated.  
        Console.WriteLine(" ");  
        Console.WriteLine("Query: " + Query1);  
        foreach (IResultObject Resource1 in ListOfResources1)  
        {  
            Console.WriteLine(Resource1["ResourceID"].IntegerValue);  
        }  

        // A slower alternative is to use the SMS_CollectionMember_a association class.  
        string Query2 = "SELECT ResourceID FROM SMS_CollectionMember_a WHERE CollectionID = 'SMS00001'";  

        // Run query.  
        IResultObject ListOfResources2 = connection.QueryProcessor.ExecuteQuery(Query2);  

        // The query returns a collection that needs to be enumerated.  
        Console.WriteLine(" ");  
        Console.WriteLine("Query: " + Query2);  
        foreach (IResultObject Resource2 in ListOfResources2)  
        {  
            Console.WriteLine(Resource2["ResourceID"].IntegerValue);  
        }  

        // A further alternative is to query the members by using the actual collection class name specified in the MemberClassName property of SMS_Collection.  
        string Query3 = "SELECT ResourceID FROM SMS_CM_Res_Coll_SMS00001";  

        // Run query.  
        IResultObject ListOfResources3 = connection.QueryProcessor.ExecuteQuery(Query3);  

        // The query returns a collection that needs to be enumerated.  
        Console.WriteLine(" ");  
        Console.WriteLine("Query: " + Query3);  
        foreach (IResultObject Resource3 in ListOfResources3)  
        {  
            Console.WriteLine(Resource3["ResourceID"].IntegerValue);  
        }  
    }  

    catch (SmsException eX)  
    {  
        Console.WriteLine("Failed to run queries. Error: " + eX.Message);  
        throw;  
    }  
}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

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