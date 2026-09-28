---
layout: Conceptual
title: Create an Object by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-managed-code
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Learn how to create a configuration manager object by using managed code, with included examples and links.
locale: en-us
document_id: 705c2832-04ed-8bb4-b8e5-46adbc12072b
document_version_independent_id: f368e08a-c6b4-7791-3247-1cc483f70b28
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-managed-code.md
cmProducts: []
platformId: 0d465e3e-7c48-3e81-d038-814335411aec
---

# Create an Object by Using Managed Code - Configuration Manager | Microsoft Learn

To create a Configuration Manager object by using the managed SMS Provider, use *WqlConnectionManager.CreateInstance* method. The [ConnectionManagerBase.CreateInstance](/en-us/previous-versions/system-center/developer/cc146180%28v=msdn.10%29) method takes the required object type as a string parameter and returns an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object that is used to populate the new object. The [IResultObject.Put](/en-us/previous-versions/system-center/developer/cc146500%28v=msdn.10%29) method must be called to submit the object to the SMS Provider.

### To create a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Using the **WqlConnectionManager** connection object you obtain in step one, call **[CreateInstance** to create the required the WMI object, and receive its IResultObject object instance.
3. Populate the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) properties.
4. Commit the **IResultObject** to the SMS Provider.

## Example

The following example demonstrates how to create and then populate a new Configuration Manager package (`SMS_Package`).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```csharp
public void CreatePackage(WqlConnectionManager connection)
{
    try
    {
        IResultObject package = connection.CreateInstance("SMS_Package");
        package["Name"].StringValue = "Test Package";
        package["Description"].StringValue = "A test package";
        package["PkgSourcePath"].StringValue = @"c:\Package Source";

        package.Put();
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create package. Error: " + ex.Message);
        throw;
    }
}

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: **WqlConnectionManager** | A valid connection to the SMS Provider. |

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