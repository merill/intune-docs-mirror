---
layout: Conceptual
title: Add a Context Qualifier by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code
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
description: To add a context qualifier by using the managed SMS Provider, use the Context property which is a Dictionary object that holds context qualifiers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4e59d659-662f-52e4-e6b1-8192adbfac00
document_version_independent_id: aa51e945-9408-b41b-35e0-b9902a79159d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code.md
cmProducts: []
platformId: e91ec89b-4567-9744-a122-6a23ab46d90a
---

# Add a Context Qualifier by Using Managed Code - Configuration Manager | Microsoft Learn

In Configuration Manager, to add a context qualifier by using the managed SMS Provider, use the [Context](/en-us/previous-versions/system-center/developer/cc147087%28v=msdn.10%29) property which is a `Dictionary` object that holds context qualifiers.

Typically you will add your application name to the ApplicationName context qualifier, along with the computer name (MachineName) and Locale identifier (LocaleID).

### To add Configuration Manager context qualifier

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code)
2. Get the [SmsNamedValuesDictionary](/en-us/previous-versions/system-center/developer/cc147435%28v=msdn.10%29) object from the *WqlConnectionManager* object that you get from step 1.
3. Add the context qualifiers as required.

## Example

The following C# example first adds a number of context qualifiers to a WQLConnectionManager object *Context* dictionary property. It then displays a list of the context qualifiers in dictionary object.

Note

**WqlConnectionManager** derives from **ConnectionManagerBase**.

In the example, the `LocaleID` context qualifier is hard-coded to English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void AddContextQualifiers(WqlConnectionManager connection)
{
    try
    {
        connection.Context.Add("ApplicationName", "My application name");
        connection.Context.Add("MachineName","Computername");
        connection.Context.Add("LocaleID", @"MS\1033");

        foreach (KeyValuePair<string, object> namedValue in connection.Context)
        {
            Console.WriteLine(namedValue.Key);
            Console.WriteLine(namedValue.Value);
            Console.WriteLine();
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to add context qualifier : " + e.Message);
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - WqlConnectionManager | A valid connection to the SMS Provider. |

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