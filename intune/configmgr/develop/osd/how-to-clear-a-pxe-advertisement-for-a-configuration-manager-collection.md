---
layout: Conceptual
title: Clear a PXE Advertisement For a Collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection
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
description: To clear a PXE advertisement for a Configuration Manager collection, you call the ClearLastNBSAdvForCollection Method in Class SMS_Collection
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6f89bec6-ec8a-95e4-6117-def19ff1e610
document_version_independent_id: 23ae98ea-3099-075d-7898-2dd362910fd1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: c66e814b-b71c-4930-95ef-966fe4548949
---

# Clear a PXE Advertisement For a Collection - Configuration Manager | Microsoft Learn

To clear a PXE advertisement for a Configuration Manager collection, you call the [ClearLastNBSAdvForCollection Method in Class SMS_Collection](../reference/core/clients/collections/clearlastnbsadvforcollection-method-in-class-sms_collection) method.

Clearing a PXE advertisement forces the PXE server to re-evaluate the mandatory advertisement that a PXE device must execute on the next PXE boot. It is most often used when the last advertisement that was executed failed or when the advertisement must be re-run. For information about clearing the PXE advertisement for a resource, see [How to Clear a PXE Advertisement for a Configuration Manager Resource](how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource).

### To clear a PXE advertisement for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_Collection](../reference/core/clients/collections/sms_collection-server-wmi-class) object for the collection you want to clear the PXE advertisement for.
3. Call the `ClearLastNBSAdvForCollection` method to clear the PXE advertisement for the collection.

## Example

The following example clears the PXE advertisement for the collection that is identified by the `collectionID` parameter.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub ClearPxeAdvertisementCollection (connection, collectionID)

    On Error Resume Next
    Dim collection

    ' Get the collection.
    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")

    result = collection.ClearLastNBSAdvForCollection

    if Err.number <> 0 Then
        WScript.Echo "Failed to clear PXE advertisement for collection: " & collectionID
        Exit Sub
    End If

End Sub
```

```c
public void ClearPxeAdvertisementCollection(WqlConnectionManager connection, string collectionID)
{
    try
    {
        // Get the collection.
        IResultObject collection = connection.GetInstance(@"SMS_Collection.CollectionID='" + collectionID + "'");

        Dictionary<string, object> inParams = new Dictionary<string, object>();
        IResultObject outParams = collection.ExecuteMethod("ClearLastNBSAdvForCollection", inParams);

        if (outParams == null || outParams["StatusCode"].IntegerValue != 0)
        {
            Console.WriteLine
                ("Failed to clear PXE advertisement for collection " + collection["Name"].ToString());
            return;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to clear PXE advertisement " + e.Message);
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `collectionID` | - Managed: `String`- VBScript: `String` | The resource identifier. You can obtain this from the `SMS_Collection` class CollectionID property. |

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

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).