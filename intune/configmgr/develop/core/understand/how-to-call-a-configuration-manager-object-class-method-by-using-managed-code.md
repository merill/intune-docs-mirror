---
layout: Conceptual
title: Call an Object Class Method by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-managed-code
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
description: To call a SMS Provider class method in Configuration Manager, use the ExecuteMethod method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9f56a096-dde2-b80f-2106-7cf70cecd3b8
document_version_independent_id: 4b11fa08-7269-ce33-8671-1e3b5b6067e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-managed-code.md
cmProducts: []
platformId: b8719619-188f-cb03-a17b-5660d095dbff
---

# Call an Object Class Method by Using Managed Code - Configuration Manager | Microsoft Learn

To call a SMS Provider class method, in Configuration Manager, you use the [ExecuteMethod](/en-us/previous-versions/system-center/developer/cc146186%28v=msdn.10%29) method. You populate a [Dictionary](/en-us/previous-versions/visualstudio/visual-studio-6.0/aa239680%28v=vs.60%29) object with the method's parameters, and the return value is an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object that contains the result of the method call.

Note

To call a method on an object instance, use the [ExecuteMethod](/en-us/previous-versions/system-center/developer/cc146233%28v=msdn.10%29) method on the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object instance.

### To call a Configuration Manager object class method

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Create the input parameters as a **Dictionary** object.
3. Using the **WqlConnectionManager** object instance, call [ExecuteMethod](/en-us/previous-versions/system-center/developer/cc146186%28v=msdn.10%29) and specify the class name and input parameters.
4. Retrieve the method return value from the *ReturnValue* property in the returned **IResultObject** object.

## Example

The following example validates a collection rule query by calling the [SMS_CollectionRuleQuery](../../reference/core/clients/collections/sms_collectionrulequery-server-wmi-class) class [ValidateQuery](../../reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery) class method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void ValidateQueryRule(WqlConnectionManager connection, string wqlQuery)
{
    try
    {
        Dictionary<string,object> validateQueryParameters = new Dictionary<string,object>();

        // Add the sql query as the WQLQuery parameter.
        validateQueryParameters.Add("WQLQuery",wqlQuery);

        // Call the method
        IResultObject result=connection.ExecuteMethod("SMS_CollectionRuleQuery", "ValidateQuery", validateQueryParameters);

        if (result["ReturnValue"].BooleanValue == true)
        {
            Console.WriteLine (wqlQuery + " is a valid query");
        }
        else
        {
            Console.WriteLine (wqlQuery + " is not a valid query");
        }
     }
     catch (SmsException ex)
     {
           Console.WriteLine("Failed to validate query rule: ",ex.Message);
           throw;
     }
}

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: **WqlConnectionManager** | A valid connection to the SMS Provider. |
| `wqlQuery` | - Managed: **IResultObject** | A WQL query string. For this example, `SELECT * FROM SMS_R_System` is a valid query. |

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