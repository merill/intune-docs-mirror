---
layout: Conceptual
title: Enable or Disable a Windows Driver - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enable-or-disable-a-windows-driver
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
description: Enable or disable a Windows driver in the operating system deployment driver catalog by setting the IsEnabled property of the SMS_Driver Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9851f49f-401a-0c4b-8f8b-c9a00b6515df
document_version_independent_id: 5ba8b6cb-2584-9037-adca-201aea96340b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-enable-or-disable-a-windows-driver.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-enable-or-disable-a-windows-driver
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-enable-or-disable-a-windows-driver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 887409e7-a37c-047b-adf5-c5fdbbfeb953
---

# Enable or Disable a Windows Driver - Configuration Manager | Microsoft Learn

You enable or disable a Windows driver in the operating system deployment driver catalog, in Configuration Manager, by setting the `IsEnabled` property of the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object. A driver can be disabled to prevent it from being installed by the Auto Apply Driver action in a task sequence.

### To enable or disable a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the `SMS_Driver` object for the driver you want to enable or disable.
3. Set the `IsEnabled` property to `true` to enable the driver, or to `false` to disable the driver.
4. Commit the `SMS_Driver` object changes.

## Example

The following example method enables or disables a driver depending on the value of the `enableDriver` parameter.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub EnableDriver(connection,driverID,vEnableDriver)

        ' Get the driver.
        Set driver = connection.Get("SMS_Driver.CI_ID=" & driverID)

        ' Set the flag.
        driver.IsEnabled=vEnableDriver

        ' Commit changes.
        driver.Put_

End Sub
```

```c
public void EnableDriver(
    WqlConnectionManager connection,
    int driverID,
    bool enableDriver)
{
    try
    {
        // Get the driver.
        IResultObject driver = connection.GetInstance("SMS_Driver.CI_ID=" + driverID);

        // Set the flag.
        driver["IsEnabled"].BooleanValue = enableDriver;

        // Commit the changes.
        driver.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driverID` | - Managed: `Integer`- VBScript: `Integer` | The Windows driver identifier available in `SMS_Driver.CI_ID`. |
| `enableDriver` | - Managed: `String`- VBScript: `String` | Flag to enable or disable the driver.`true` - The driver is enabled.`false` - The driver is disabled. |

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