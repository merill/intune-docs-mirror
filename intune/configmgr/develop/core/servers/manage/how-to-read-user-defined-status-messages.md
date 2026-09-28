---
layout: Conceptual
title: Read User-Defined Status Messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-read-user-defined-status-messages
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
description: In Configuration Manager, you can read user-defined status messages, on the site server, by querying the SMS Provider.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8022266b-9899-e093-2c39-6c9e86ba0ee7
document_version_independent_id: f19fb025-fa40-81ca-2471-ca5c1e480cdf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-read-user-defined-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-read-user-defined-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-read-user-defined-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 01a81f8e-5688-2e12-1cc5-3be18ccb3e94
---

# Read User-Defined Status Messages - Configuration Manager | Microsoft Learn

In Configuration Manager, you can read user-defined status messages, on the site server, by querying the SMS Provider.

### To read a user-defined status messages

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Query the provider for the SMS`_StatusMessage` instances you want. As part of the query get the insertion string values from `SMS_SMS_StatMsgInStrings` and the attribute value from `SMS_StatMsgAttributes`.

## Example

The following example reads error message status messages for the sample created in [How to Report User-Defined Status Messages Using WMI](how-to-report-user-defined-status-messages). Make sure the `MyPackageID` and `MyApplication` values in the query match in both samples.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub ReadErrorStatusMesage(connection)

    Dim queryWQL
    Dim message
    Dim messageSet
    Dim statusMessage
    Dim insertionString
    Dim attributes

    queryWQL = "SELECT b.Component, b.MachineName, b.MessageType, b.MessageID, " & _
            "       c.InsStrValue, d.AttributeValue " & _
            "FROM SMS_StatusMessage b " & _
            "     JOIN SMS_StatMsgInsStrings c ON b.RecordID = c.RecordID " & _
            "     JOIN SMS_StatMsgAttributes d ON c.RecordID = d.RecordID " & _
            "WHERE b.Component = 'MyApplication' " & _
            "AND   d.AttributeID = 400 " & _
            "AND   d.AttributeValue = 'MyPackageID' "

    Set messageSet = connection.ExecQuery(queryWQL)

    For Each message in messageSet

        ' Get the message objects.
        statusMessage = message.Properties_.Item("b")
        insertionString = message.Properties_.Item("c")
        attributes = message.Properties_.Item("d")

        ' Display the message details.
        WScript.Echo "Message: " + insertionString.Properties_.Item("insstrvalue")
        WScript.Echo "Component: " + statusMessage.Properties_.Item("Component")
        WScript.Echo "Computer: " + statusMessage.Properties_.Item("MachineName")
        WScript.Echo "MessageID: " + Cstr(statusMessage.Properties_.Item("MessageID"))
        WScript.Echo attributes.Properties_.Item("attributevalue")
        WScript.Echo

    Next

 End Sub

```

```c
public void ReadErrorStatusMessage(WqlConnectionManager connection)
{
    try
    {
        string queryWQL = "SELECT b.Component, b.MachineName, " +
                "       b.MessageType, b.MessageID, " +
                "       c.insstrvalue, d.attributevalue " +
                "FROM SMS_StatusMessage b " +
                "     JOIN SMS_StatMsgInsStrings c ON b.RecordID = c.RecordID " +
                "     JOIN SMS_StatMsgAttributes d ON c.RecordID = d.RecordID " +
                "WHERE b.Component = \"MyApplication\" " +
                "AND   d.AttributeID = 400 " +
                "AND   d.AttributeValue = \"MyPackageID\" ";

        IResultObject query = connection.QueryProcessor.ExecuteQuery(queryWQL);
        foreach (IResultObject o in query)
        {

            ManagementBaseObject  statusMessage = (ManagementBaseObject)o["b"].ObjectValue;
            ManagementBaseObject insertionString = (ManagementBaseObject)o["c"].ObjectValue;
            ManagementBaseObject attributes = (ManagementBaseObject)o["d"].ObjectValue;

            Console.WriteLine("Message: " + insertionString["insstrvalue"]);
            Console.WriteLine("Component: " + statusMessage["Component"]);
            Console.WriteLine("Computer: " + statusMessage["MachineName"]);
            Console.WriteLine("MessageID: " + statusMessage["MessageID"]);
            Console.WriteLine(attributes["attributevalue"]);
            Console.WriteLine();
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to read status message: ", ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](../../understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals). |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

System.Management

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../configure/role-based-administration).