---
layout: Conceptual
title: Delete Status Messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-delete-status-messages
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
description: In Configuration Manager, you delete status messages by calling the SMS_StatusMessage class DeleteByID method and supplying an array of status message RecordID identifiers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 80d5f5b5-b497-1599-e4de-51a29d2e8ae4
document_version_independent_id: 4deb672f-a405-f041-2d2f-a9f85d8ea908
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-delete-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-delete-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-delete-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 47147400-46fe-93fb-bd5e-338bb652849f
---

# Delete Status Messages - Configuration Manager | Microsoft Learn

In Configuration Manager, you delete status messages by calling the `SMS_StatusMessage` class `DeleteByID` method and supplying an array of status message `RecordID` identifiers. Alternatively, you can call the `SMS_StatusMessage` class `DeleteByQuery` method and supply a WQL query that identifies the status messages to be deleted.

### To delete a status message

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Call the `SMS_StatusMessage` class `DeleteByID` method with an array of record identifiers for the status messages to be deleted.

## Example

The following example deletes a single status message identified by the `recordId` identifier.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub DeleteStatusMessage(connection, recordId)

    Dim inParams
    Dim outParams
    Dim statusMessageClass

    On Error Resume Next

    ' Obtain the class definition object of a SMS_StatusMessage object.
    Set statusMessageClass = connection.Get("SMS_StatusMessage")

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get status message class"
        Exit Sub
    End If

    ' Set up the in parameter.
    Set inParams = statusMessageClass.Methods_("DeleteByID").InParameters.SpawnInstance_
    inParams.RecordIDs = Array(recordId)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get in parameters object"
        Exit Sub
    End If

    ' Call the method.
    Set outParams = _
        connection.ExecMethod( "SMS_StatusMessage", "DeleteByID", inParams)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't run method"
        Exit Sub
    End If

    WScript.Echo CStr(outParams.ReturnValue) + " record(s) deleted"

  End Sub
```

```c
public void DeleteStatusMessage(WqlConnectionManager connection, Int64 recordId)
{
    try
    {
        Dictionary<string, object> StatusMessageParameters = new Dictionary<string, object>();

         // Add the parameters.
        StatusMessageParameters.Add("RecordIDs", new Int64[] { recordId });

        // Call the method.
        IResultObject result = connection.ExecuteMethod("SMS_StatusMessage", "DeleteByID", StatusMessageParameters);

        Console.WriteLine (result["ReturnValue"].IntegerValue + " record(s) deleted");

   }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to delete error message: ", ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: [WqlConnectionManager](../../understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals). |
| `recordId` | - Managed: `Integer`- VBScript: `Integer` | The status message identifier. This is `SMS_StatusMessage` object `RecordID` property for the status message to be deleted. |

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

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../configure/role-based-administration).