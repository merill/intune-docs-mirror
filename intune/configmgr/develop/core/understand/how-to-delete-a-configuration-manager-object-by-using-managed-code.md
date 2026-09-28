---
layout: Conceptual
title: Delete an Object by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-managed-code
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
description: Learn how to create a Configuration Manager object by using the managed SMS Provider with WqlConnectionManager.CreateInstance method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6c7f5a03-ec8a-74d9-7734-cb4d6b55b1b6
document_version_independent_id: 517391bd-3344-cd2b-9edf-2e284ece6187
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-managed-code.md
cmProducts: []
platformId: fb93ce8d-3bf7-851a-4a16-52eb86307c40
---

# Delete an Object by Using Managed Code - Configuration Manager | Microsoft Learn

To delete a Configuration Manager object by using the managed SMS Provider, use the [IResultObject.Delete](/en-us/previous-versions/system-center/developer/cc146496%28v=msdn.10%29) method. You can get a [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object for a Configuration Manager object in numerous ways. For more information, see [How to Read a Configuration Manager Object by Using Managed Code](how-to-read-a-configuration-manager-object-by-using-managed-code)

### To delete a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Using the `WqlConnectionManager` object you obtain in step one, call the `GetInstance` method to get the `IResultObject` object for the Configuration Manager object.
3. Call the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object [Delete](/en-us/previous-versions/system-center/developer/cc146496%28v=msdn.10%29) method to delete the Configuration Manager object.

## Example

The following example deletes a package by using the supplied package identifier. This example uses the **WqlConnectionManager** class **GetInstance** method to get an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object for the Configuration Manager package and then deletes the package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void DeletePackage(WqlConnectionManager connection, string packageID)
{
    try
    {
        IResultObject package = connection.GetInstance(@"SMS_Package.PackageID='" + packageID + "'");
        package.Delete();
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to delete package: " + ex.Message);
        throw;
    }
}

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - **WqlConnectionManager** | A valid connection to the SMS Provider. |
| `PackageID` | - `String` | The package identifier for an existing package. This can be obtained from the [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class) class *PackageID* property. |

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