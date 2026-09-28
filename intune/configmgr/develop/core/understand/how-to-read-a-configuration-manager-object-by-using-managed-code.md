---
layout: Conceptual
title: Read an Object by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code
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
description: The GetInstance method takes a string that identifies a specific object instance and returns an IResultObject that is used to access the object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a23b6af7-0652-a38b-f661-84059fea72fb
document_version_independent_id: fc1d0292-f84c-5de1-222c-225d6a87aa48
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 8fd79538-cdf8-68d2-4417-4a9acda83093
---

# Read an Object by Using Managed Code - Configuration Manager | Microsoft Learn

To read a Configuration Manager object instance by using the managed SMS Provider, use *WqlConnectionManager.GetInstance*. The [GetInstance](/en-us/previous-versions/system-center/developer/cc146190%28v=msdn.10%29) method takes a string that identifies a specific object instance and returns an [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object that is used to access the object.

The following example function shows the name and description for a supplied package identifier.

### To read a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Call WqlConnectionManager class [GetInstance](/en-us/previous-versions/system-center/developer/cc146190%28v=msdn.10%29) method to get the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object for the object you want.
3. Display the properties of the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29).

## Example

The following code example shows how to read a Configuration Manager object.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void DisplayPackageName(WqlConnectionManager connection, string packageID)
{
    try
    {
        // Get the package.
        IResultObject package = connection.GetInstance(@"SMS_Package.PackageID='" + packageID + "'");
        Console.WriteLine("Package Name: " + package["Name"].StringValue);
        Console.WriteLine("Package Description: " + package["Description"].StringValue);
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
| `Connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `PackageID` | Managed: `String` | A valid package identifier. Obtained from the [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class) class PackageID property. |

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