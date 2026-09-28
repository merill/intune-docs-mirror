---
layout: Conceptual
title: Delete a Windows Driver - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-delete-a-windows-driver-from-configuration-manager
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
description: You delete a Windows driver from the operating system deployment driver catalog, in Configuration Manager, by deleting its SMS_Driver Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 08abfe21-9d02-9a6f-61e9-effbded55749
document_version_independent_id: 95365e5e-e92b-339c-7259-c7cfe2aa7438
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-delete-a-windows-driver-from-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-delete-a-windows-driver-from-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-delete-a-windows-driver-from-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b869876c-9c97-70ed-af0e-ac7af005b709
---

# Delete a Windows Driver - Configuration Manager | Microsoft Learn

You delete a Windows driver from the operating system deployment driver catalog, in Configuration Manager, by deleting its [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object. When you delete a driver, its definition is deleted, and it is no longer matched by the apply driver action task sequences. However, if the content associated with the driver was added to a driver package, or if the driver was added to a boot image package, the content remains there until the packages are updated.

### To delete a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the `SMS_Driver` object for the driver that you want to delete.
3. Delete the `SMS_Driver` object.

## Example

The following example method deletes a driver identified by its `CI_ID` property value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub DeleteDriver(connection,driverID)

        ' Get the driver.
        Set driver = connection.Get("SMS_Driver.CI_ID=" & driverID)

        ' Commit changes.
        driver.Delete_

End Sub
```

```c

public void DeleteDriver(WqlConnectionManager connection,
                         int driverID)
{
    try
    {
        // Get the driver.
        IResultObject driver = connection.GetInstance("SMS_Driver.CI_ID=" + driverID);

        // Delete the driver.
        driver.Delete();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to delete driver: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed:`WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driverID` | - Managed: `Integer`- VBScript: `Integer` | The Windows driver identifier available in `SMS_Driver.CI_ID`. |

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