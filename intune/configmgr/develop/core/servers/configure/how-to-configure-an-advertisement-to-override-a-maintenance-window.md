---
layout: Conceptual
title: Configure an Advertisement to Override a Maintenance Window - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-an-advertisement-to-override-a-maintenance-window
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
description: Configure an advertisement to override maintenance windows using the SMS_Advertisement class and the AdvertFlags class property in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 127fec3d-413c-96f8-1981-b7f93f4f2d82
document_version_independent_id: 9ae82309-3def-26aa-7250-5afb1d9da094
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-an-advertisement-to-override-a-maintenance-window.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-an-advertisement-to-override-a-maintenance-window
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-an-advertisement-to-override-a-maintenance-window.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cc868c14-a90f-330c-2942-d157534a0078
---

# Configure an Advertisement to Override a Maintenance Window - Configuration Manager | Microsoft Learn

The following example shows how to configure an advertisement to override service windows using the `SMS_Advertisement` class and the `AdvertFlags` class property in Configuration Manager.

### To configure an advertisement to override maintenance windows

1. Set up a connection to the SMS Provider.
2. Load an existing advertisement object using the `SMS_Advertisement` class.
3. Modify the `AdvertFlags` property using the hexadecimal value for `OVERRIDE_MAINTENANCE_WINDOW`.
4. Save the modified advertisement and properties.

## Example

The following example method configures an existing advertisement to override maintenance windows.

Important

The hexadecimal values that define the `AdvertFlags` property are listed in the `SMS_Advertisement` class reference material.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ModifyAdvertisementToOverrideMaintenanceWindows(connection, existingAdvertisementID)

    ' Define a constant with the hexadecimal value for the OVERRIDE_MAINTENANCE_WINDOW.
    Const OVERRIDE_MAINTENANCE_WINDOWS = &H00100000
    Dim advertisementToModify

    ' Get the specific advertisement instance to modify.
    Set advertisementToModify = connection.Get("SMS_Advertisement.AdvertisementID='" & existingAdvertisementID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Advertisement Name:            " & advertisementToModify.AdvertisementName
    Wscript.Echo "Advertisement Flags (integer): " & advertisementToModify.AdvertFlags

    ' Set the new property value.
    advertisementToModify.AdvertFlags = advertisementToModify.AdvertFlags OR OVERRIDE_MAINTENANCE_WINDOWS

    ' Save the advertisement.
    advertisementToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Values after change:  "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Advertisement Name:             " & advertisementToModify.AdvertisementName
    Wscript.Echo "Advertisement Flags (integer):  " & advertisementToModify.AdvertFlags

End Sub

```

```c

public void ModifySWDAdvertisementToOverrideMaintenanceWindows(WqlConnectionManager connection,
                                                               string existingAdvertisementID)
{
    // Define a constant with the hexadecimal value for OVERRIDE_MAINTENANCE_WINDOW.
    const Int32 OVERRIDE_MAINTENANCE_WINDOWS = 0x00100000;

    try
    {
        // Get the specific advertisement instance to modify.
        IResultObject advertisementToModify = connection.GetInstance(@"SMS_Advertisement.AdvertisementID='" + existingAdvertisementID + "'");

        // List the existing property values.
        Console.WriteLine();
        Console.WriteLine("Values before change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Advertisement Name:            " + advertisementToModify["AdvertisementName"].StringValue);
        Console.WriteLine("Advertisement Flags (integer): " + advertisementToModify["AdvertFlags"].IntegerValue);

        // Modify the AdvertFlags value to include the OVERRIDE_MAINTENANCE_WINDOWS value.
        advertisementToModify["AdvertFlags"].IntegerValue = advertisementToModify["AdvertFlags"].IntegerValue | OVERRIDE_MAINTENANCE_WINDOWS;

        // Save the advertisement with the new value.
        advertisementToModify.Put();

        // Reload the advertisement to verify the change.
        advertisementToModify.Get();

        // List the existing (modified) property values.
        Console.WriteLine();
        Console.WriteLine("Values after change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Advertisement Name:            " + advertisementToModify["AdvertisementName"].StringValue);
        Console.WriteLine("Advertisement Flags (integer): " + advertisementToModify["AdvertFlags"].IntegerValue);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to modify advertisement. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingAdvertisementID` | - Managed: `String`- VBScript: `String` | The ID of the advertisement to modify. |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

mscorlib

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).