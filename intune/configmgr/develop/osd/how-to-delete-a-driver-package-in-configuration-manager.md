---
layout: Conceptual
title: Delete a Driver Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-delete-a-driver-package-in-configuration-manager
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
description: Delete an operating system deployment driver package, in Configuration Manager, by deleting its SMS_DriverPackage.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f44d3169-470b-013c-dfb6-542d878dd290
document_version_independent_id: 41c1c461-6afa-f275-8900-4152a8ee45f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-delete-a-driver-package-in-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-delete-a-driver-package-in-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-delete-a-driver-package-in-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4247c33b-1570-7d80-86df-65da400e1b80
---

# Delete a Driver Package - Configuration Manager | Microsoft Learn

You delete an operating system deployment driver package, in Configuration Manager, by deleting its [SMS_DriverPackage](../reference/osd/sms_driverpackage-server-wmi-class) object.

Note

Windows drivers that are referenced by the driver package are not deleted.

### To delete a driver package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_DriverPackage](../reference/osd/sms_driverpackage-server-wmi-class) object for the driver that you want to delete.
3. Delete the SMS\_DriverPackage object.

## Example

The following example method deletes a driver package identified by its package identifier.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub DeleteDriverPackage(connection,packageID)

        ' Get the driver.
        Set driverPackage = connection.Get("SMS_DriverPackage.PackageID='" & packageID & "'")

        ' Delete the driver package.
        driverPackage.Delete_

End Sub
```

```c
public void DeleteDriverPackage(
    WqlConnectionManager connection,
    string packageId)
{
    try
    {
        // Get the driver package.
        IResultObject driverPackage = connection.GetInstance("SMS_DriverPackage.packageId='" + packageId + "'");

        // Delete the driver package.
        driverPackage.Delete();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to delete driver package: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `packageID` | - Managed: `String`- VBScript: `String` | - The driver package identifier available in SMS\_DriverDriverPackage.PackageID. |

## Compiling the Code

This C# example requires:

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