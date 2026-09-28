---
layout: Conceptual
title: Synchronize with the Software Update Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-synchronize-with-the-software-update-point
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
description: You synchronize the software update point, in Configuration Manager SP1, by calling the SyncNow method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e726a8dd-97ab-7268-4fb3-357535f502e0
document_version_independent_id: d8adf57e-0424-5723-6c64-ad5d9733626b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-synchronize-with-the-software-update-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-synchronize-with-the-software-update-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-synchronize-with-the-software-update-point.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: fbde9c15-eec5-1660-d579-6eb244d939a4
---

# Synchronize with the Software Update Point - Configuration Manager | Microsoft Learn

You synchronize the software update point, in Configuration Manager SP1, by calling the `SyncNow` method.

## To synchronize the software update point

1. Set up a connection to the SMS Provider.
2. Create an instance of the [SMS_SoftwareUpdate Server WMI Class](../reference/sum/sms_softwareupdate-server-wmi-class) class.
3. Create and populate the method parameter value `fullSync`.
4. Call the [SyncNow Method in Class SMS_SoftwareUpdate](../reference/sum/syncnow-method-in-class-sms_softwareupdate) method, passing in the method parameter value.

## Example

The following example method shows how to synchronize the software update point by calling the [SyncNow Method in Class SMS_SoftwareUpdate](../reference/sum/syncnow-method-in-class-sms_softwareupdate) method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```c

public void SynchronizeSoftwareUpdatePoint(WqlConnectionManager connection)
{
    try
    {

        // Create the new SMS_SoftwareUpdate object.
        IResultObject newSoftwareUpdate = connection.CreateInstance("SMS_SoftwareUpdate");

        // Create dictionary object to pass parameters to the SyncNow method.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams["fullSync"] = true;

        // Initialize the outParams object.
        IResultObject outParams = null;
        // Call SyncNow method to initiate synchronization.
        outParams = connection.ExecuteMethod("SMS_SoftwareUpdate", "SyncNow", inParams);

    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).