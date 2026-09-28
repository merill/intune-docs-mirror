---
layout: Conceptual
title: Read Lazy Properties by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi
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
description: To read a lazy property from a Configuration Manager object returned in a query, you get the object instance, which in turn retrieves any lazy object properties from the SMS Provider.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4aea4d76-8e91-1ddf-cba0-c7c708d028a3
document_version_independent_id: dce5b1af-d87a-447d-b6cf-c58a224469aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 92a67a86-3234-51a1-87fd-a916f1f2d194
---

# Read Lazy Properties by Using WMI - Configuration Manager | Microsoft Learn

To read a lazy property from a Configuration Manager object returned in a query, you get the object instance, which in turn retrieves any lazy object properties from the SMS Provider.

Note

If you know the full path to the WMI object, a call to the `SWbemServices` class `Get` method will return the WMI object along with any lazy properties. For more information, see [How to Read a Configuration Manager Object by Using WMI](how-to-read-a-configuration-manager-object-by-using-wmi).

For more information about lazy properties, see [Configuration Manager Lazy Properties](configuration-manager-lazy-properties).

### To read lazy properties

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, use the [ExecQuery](/en-us/windows/win32/wmisdk/swbemservices-execquery) object to query Configuration Manager objects.
3. Iterate through the query results.
4. Using the `SWbemServices` object you obtain from step one, call [Get](/en-us/windows/win32/wmisdk/swbemservices-get) to get the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object for each queried object you want to get lazy properties from.

## Example

The following VBScript code example queries for all [SMS_Collection](../../reference/core/clients/collections/sms_collection-server-wmi-class) objects and then displays rule names obtained from the `CollectionRules` lazy property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub ReadLazyProperty(connection)

    Dim collection
    Dim collections
    Dim collectionLazy
    Dim i

    ' Get all collections.
    Set collections = _
        connection.ExecQuery("Select * From SMS_Collection")

    For Each collection in collections

        Wscript.Echo Collection.Name

        ' Get the collection object.
        Set collectionLazy = connection.Get("SMS_Collection.CollectionID='" + collection.CollectionID + "'")

        ' Display the rule names that are in the lazy property CollectionRules.
        If IsNull(collectionLazy.CollectionRules) Then
            Wscript.Echo "No rules"
        Else
            For i = 0 To UBound(collectionLazy.CollectionRules)
                WScript.Echo "Rule " + collectionLazy.CollectionRules(i).RuleName
            Next
       End If
    Next

End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | `SWbemServices` | A valid connection to the SMS Provider. |

## Compiling the Code