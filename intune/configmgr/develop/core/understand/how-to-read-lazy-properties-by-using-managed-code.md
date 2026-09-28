---
layout: Conceptual
title: Lazy Properties by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code
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
description: To read a lazy property from a Configuration Manager object returned in a query, you get the object instance, which retrieves any lazy object properties from the SMS Provider.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6cfef5a6-fd00-eb03-aac8-6a9515fef3dc
document_version_independent_id: a4d8304a-06a5-3d8d-b2aa-2cb4fbb57a0d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code.md
cmProducts: []
platformId: 3f036243-a991-88cb-a8d6-757704ed43d7
---

# Lazy Properties by Using Managed Code - Configuration Manager | Microsoft Learn

To read a lazy property from a Configuration Manager object returned in a query, you get the object instance, which retrieves any lazy object properties from the SMS Provider.

Note

If you know the full path to the WMI object, a call to the [GetInstance](/en-us/previous-versions/system-center/developer/cc146190%28v=msdn.10%29) method returns the WMI object along with any lazy properties. For more information, see [How to Read a Configuration Manager Object by Using Managed Code](how-to-read-a-configuration-manager-object-by-using-managed-code).

For more information, see [Configuration Manager Lazy Properties](configuration-manager-lazy-properties).

### To read lazy properties

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Use **QueryProcessor** object to query Configuration Manager objects.
3. Iterate through the query results.
4. Using the **WqlConnectionManager** you obtain in step one, call [GetInstance](/en-us/previous-versions/system-center/developer/cc146190%28v=msdn.10%29) to get the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object for each queried object that you want to get lazy properties from.

## Example

The following C# code example queries for all [SMS_Collection](../../reference/core/clients/collections/sms_collection-server-wmi-class) objects and then displays rule names obtained from the `CollectionRules` lazy property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```csharp
public void ReadLazyProperty(WqlConnectionManager connection)
{
    try
    {
        // Query all collections.
        IResultObject collections = connection.QueryProcessor.ExecuteQuery("Select * from SMS_Collection");
        foreach (IResultObject collection in collections)
        {
            // Get the collection object and lazy properties.
            collection.Get();

            Console.WriteLine(collection["Name"].StringValue);

            // Get the rules.
            List<IResultObject> rules = collection.GetArrayItems("CollectionRules");
            if (rules.Count == 0)
            {
                Console.WriteLine("No rules");
                Console.WriteLine();
                continue;
            }

            foreach (IResultObject rule in rules)
            {
                // Display rule names.
                Console.WriteLine("Rule name: " + rule["RuleName"].StringValue);
            }

            Console.WriteLine();
        }
    }
    catch (SmsQueryException ex)
    {
        Console.WriteLine("Failed to get collection. Error: " + ex.Message);
        throw;
    }
}

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | `WqlConnectionManager` | A valid connection to the SMS Provider. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

Microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).