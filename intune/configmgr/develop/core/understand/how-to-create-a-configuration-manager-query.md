---
layout: Conceptual
title: Create a Query - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-query
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
description: Create an SMS_Query-based query by creating an instance of SMS_Query. The SMS_Query class Expression object defines a WQL query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c0838d0a-8aad-35ed-ff5a-11d545531989
document_version_independent_id: d8739d9c-5c50-9912-f31b-387a0245467e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-query.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-create-a-configuration-manager-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-query.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 4d5b50e3-fee7-ae85-c3ee-f1dce7f48a60
---

# Create a Query - Configuration Manager | Microsoft Learn

In Configuration Manager, you create an `SMS_Query`-based query by creating an instance of `SMS_Query`. The `SMS_Query` class `Expression` object defines a WQL query. If you want to limit the query results to a specific collection, specify the collection identifier in the `LimitToCollectionID` property.

Note

When you create a query, it is displayed in the Configuration Manager console under **Queries**.

### To create a query

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Create an instance of [SMS_Query](../../reference/core/clients/manage/sms_query-server-wmi-class).
3. Populate the `SMS_Query` properties.
4. Commit the `SMS_Query`.
5. If required, retrieve the query object and get the query identifier.

## Example

The following example method creates an `SMS_Query` class query that queries for all systems. The method returns the query identifier, which can be used as input to the example in [How to Run a Configuration Manager Query](how-to-run-a-query).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Function CreateQuery(connection)
   On Error Resume Next

   Dim query
   Dim path

   ' Create a query object.
    Set query = connection.Get("SMS_Query").SpawnInstance_()

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't create query object"
        CreateQuery = Null
        Exit Function
    End If

    ' Populate the object.
    query.Comments = "A query for all systems"
    query.Expression = "select Name, " + _
    "SMSAssignedSites, " +              _
    "IPAddresses, " +                   _
    "IPSubnets, " +                     _
    "OperatingSystemNameandVersion, " + _
    "ResourceDomainORWorkgroup, " +     _
    "LastLogonUserDomain, " +           _
    "LastLogonUserName, " +             _
    "SMSUniqueIdentifier, " +           _
    "ResourceId, " +                    _
    "ResourceType, " +                  _
    "NetbiosName " +                    _
    "from sms_r_system"
    query.LimitToCollectionID = nothing
    query.Name = "Query All Systems"
    query.TargetClassName = "SMS_R_System"

    ' Commit the object
    path = query.Put_

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't commit the query"
        CreateQuery = Null
        Exit Function
    End If

    WScript.Echo "Query created"

    ' Get the object back to get the query identifier.
    Set query = connection.Get(path)
    CreateQuery = query.QueryID

End Function

```

```c
public string CreateQuery(WqlConnectionManager connection)
{
    try
    {
        // Create an SMS_Query object.
        IResultObject query = connection.CreateInstance("SMS_Query");

        // Populate the object.
        query["Comments"].StringValue = "A query for all systems";
        query["Expression"].StringValue =
            "select Name, " +
            "SMSAssignedSites, " +
            "IPAddresses, " +
            "IPSubnets, " +
            "OperatingSystemNameandVersion, " +
            "ResourceDomainORWorkgroup, " +
            "LastLogonUserDomain, " +
            "LastLogonUserName, " +
            "SMSUniqueIdentifier, " +
            "ResourceId, " +
            "ResourceType, " +
            "NetbiosName " +
            "from sms_r_system";
        query["LimitToCollectionID"].StringValue = null;
        query["Name"].StringValue = "Query All Systems";
        query["TargetClassName"].StringValue = "SMS_R_System";

        // Commit the query.
        query.Put();

        // Get the query - allows access to the queryID.
        query.Get();

        // Return the query identifier.
        return query["QueryID"].StringValue;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to run the query: " + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | - A valid connection to the SMS Provider. |

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