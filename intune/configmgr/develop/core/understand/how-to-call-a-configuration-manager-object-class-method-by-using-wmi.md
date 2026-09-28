---
layout: Conceptual
title: Call an Object Class Method by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi
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
description: To call a SMS Provider class method, use the SWbemServices object ExecMethod method to call methods that are defined by the class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ce14d43c-845f-a339-6dd7-7e79f189f47b
document_version_independent_id: 5cb2f922-d5d2-667a-f236-67a444a324d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d3af4c92-fbea-2b09-d5ca-24dcee264faf
---

# Call an Object Class Method by Using WMI - Configuration Manager | Microsoft Learn

To call a SMS Provider class method, in Configuration Manager, you use the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object [ExecMethod](/en-us/windows/win32/wmisdk/swbemservices-execmethod) method to call methods that are defined by the class.

Note

To call a method on an object instance, call the method from the object directly. For example, `ObjectInstance.MethodName parameters`.

### To call a Configuration Manager object class method

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Using the SWbemServices you obtain in step one, call [Get](/en-us/windows/win32/wmisdk/swbemservices-get) to get the class definition.
3. Create the input parameters as a [SWbemMethodSet](/en-us/windows/win32/wmisdk/swbemmethodset).
4. Using the SWbemServices object instance, call [ExecMethod](/en-us/windows/win32/wmisdk/swbemservices-execmethod) and specify the class name and input parameters.
5. Retrieve the method return value from the *ReturnValue* property in the returned [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object.

## Example

The following example validates a collection rule query by calling the [SMS_CollectionRuleQuery](../../reference/core/clients/collections/sms_collectionrulequery-server-wmi-class) class [ValidateQuery](../../reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery) class method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub ValidateQueryRule(connection, wqlQuery)

    Dim inParams
    Dim outParams
    Dim collectionRuleClass

    On Error Resume Next

    ' Obtain the class definition object of a SMS_CollectionRuleQuery object.
    Set collectionRuleClass = connection.Get("SMS_CollectionRuleQuery")

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get collection rule query object"
        Exit Sub
    End If

    ' Set up the in parameter.
    Set inParams = collectionRuleClass.Methods_("ValidateQuery").InParameters.SpawnInstance_
    inParams.WQLQuery = wqlQuery
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get in parameters object"
        Exit Sub
    End If

    ' Call the method.
    Set outParams = _
        connection.ExecMethod( "SMS_CollectionRuleQuery", "ValidateQuery", inParams)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't run method"
        Exit Sub
    End If

    If outParams.ReturnValue = True Then
        Wscript.Echo "Valid query"
    Else
        WScript.Echo "Not a valid query"
    End If
  End Sub

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `wqlQuery` | - `String` | A WQL query string. For this example, `SELECT * FROM SMS_R_System` is a valid query. |

## Compiling the Code