---
layout: Conceptual
title: Report User-Defined Status Messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages
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
description: Learn how to report user-defined informational, warning, and error status messages, on the site server using methods defined in the SMS_StatusMessage class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 57988f97-b369-c3fe-cf77-8820d9e35ee5
document_version_independent_id: 7423fe2b-4969-af84-7602-eaa93dbd122b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 4ce78579-79b9-355d-a204-e7656d7956f3
---

# Report User-Defined Status Messages - Configuration Manager | Microsoft Learn

In Configuration Manager, you can report user-defined informational, warning, and error status messages, on the site server, by using the following methods that are defined in the `SMS_StatusMessage` class:

| Method | Description |
| --- | --- |
| `RaiseErrorStatusMsg` | Raises an error status message. |
| `RaiseWarningStatusMsg` | Raises a warning status message. |
| `RaiseInformationalStatusMsg` | Raises an informational status message. |

### To report a user defined status message by using WMI

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Call the `SMS_StatusMessage` class method that is appropriate for the type of status message you want to raise.

## Example

The following example raises an error message. It also defines an attribute identifier and attribute values for a package. For more information about attributes, see [SMS_StatMsgAttributes Server WMI Class](../../../reference/core/servers/manage/sms_statmsgattributes-server-wmi-class).

In the example, the `LocaleID` property is hard-coded to English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../../../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub RaiseErrorStatusMessage(connection)

    Dim smsContext
    Dim statusMessageParameters
    Dim inParams
    Dim statusMessageClass

    Set smsContext = CreateObject("WbemScripting.SWbemNamedValueSet")

    ' Add the context qualifiers to the set.
    smsContext.Add "LocaleID", "MS\1033"
    smsContext.Add "MachineName", "MyComputerName"
    smsContext.Add "ApplicationName", "MyApplication"

   ' Obtain the class definition object of a SMS_Status Message object.
    Set statusMessageClass = connection.Get("SMS_StatusMessage")

    ' Set up the in parameter.
    Set inParams = statusMessageClass.Methods_("RaiseErrorStatusMsg").InParameters.SpawnInstance_
    inParams.MessageText = "This is an error message"
    inParams.MessageType = 768
    inParams.AttrIDs = Array(400)
    inParams.AttrValues = Array("MyPackageID")

    Call connection.ExecMethod( "SMS_StatusMessage", "RaiseErrorStatusMsg", inParams,,smsContext)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't run method"
        Exit Sub
    End If

 End Sub
```

```c
public void RaiseErrorStatusMessage(WqlConnectionManager connection)
{
    try
    {
        Dictionary<string, object> StatusMessageParameters = new Dictionary<string, object>();

        connection.Context.Add("ApplicationName", "MyApplication");
        connection.Context.Add("MachineName", "MyComputerName");
        connection.Context.Add("LocaleID", @"MS\1033");

        // Add the parameters.
        StatusMessageParameters.Add("MessageText", "This is an error message");
        StatusMessageParameters.Add("MessageType", 768);
        StatusMessageParameters.Add("AttrIDs", new int[] { 400 });
        StatusMessageParameters.Add("AttrValues", new string[] { "MyPackageID" });

        // Call the method.
        connection.ExecuteMethod("SMS_StatusMessage", "RaiseErrorStatusMsg", StatusMessageParameters);

    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to raise error status message: ", ex.Message);
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

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../configure/role-based-administration).