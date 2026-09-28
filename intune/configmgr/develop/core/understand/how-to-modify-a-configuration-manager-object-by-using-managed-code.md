---
layout: Conceptual
title: Modify an Object by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-managed-code
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
description: Learn how to modify a configuration manager object by using managed code with the provided examples and links.
locale: en-us
document_id: b439265b-11e6-3312-bac7-3f20b4090383
document_version_independent_id: 7280795f-d66f-249b-c73b-246639d2fb4e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-managed-code.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: c6f0ed98-602b-9229-80bc-15b4e0521c1c
---

# Modify an Object by Using Managed Code - Configuration Manager | Microsoft Learn

To modify a Configuration Manager object instance by using the managed SMS Provider, use the object's [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) interface to make modifications. You then call the [IResultObject.Put](/en-us/previous-versions/system-center/developer/cc146500%28v=msdn.10%29) method to submit the changes.

Note

The IResultObject interface for an object can be obtained through the WqlConnectionManager.GetInstance method or through other queries. For an example that uses asynchronous queries, see [How to Perform an Asynchronous Configuration Manager Query Using Managed Code](how-to-perform-an-asynchronous-query-by-using-managed-code).

### To modify a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Using the **WqlConnectionManager** object you obtain in step one, call *GetInstance* to get an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) for the required object.
3. Make changes to object using the IResultObject.
4. Commit the changes to the SMS provider with the IResultObject object [Put](/en-us/previous-versions/system-center/developer/cc146500%28v=msdn.10%29) method.

## Example

The following example function updates a package's description from a supplied package identifier and description.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```

public void ModifyPackageDescription(WqlConnectionManager connection, string packageID, string description)
{
    try
    {
        IResultObject package = connection.GetInstance(@"SMS_Package.PackageID='" + packageID + "'");
        Console.WriteLine("Package Name: " + package["Name"].StringValue);
        Console.WriteLine("Current Description: " + package["Description"].StringValue);

        package["Description"].StringValue = description;

        package.Put();

        Console.WriteLine("New description: " + package["Description"].StringValue);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to get package. Error: " + ex.Message);
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

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).