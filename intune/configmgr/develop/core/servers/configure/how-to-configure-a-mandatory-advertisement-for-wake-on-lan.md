---
layout: Conceptual
title: Configure a Mandatory Advertisement for Wake On LAN - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-a-mandatory-advertisement-for-wake-on-lan
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
description: Learn how to configure an existing mandatory advertisement for Wake On LAN by using the SMS_Advertisement class and properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 23e39633-ee74-bfc7-930b-6413a43f3986
document_version_independent_id: f6cccfee-bfac-a81c-2511-64535542cefa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-a-mandatory-advertisement-for-wake-on-lan.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-a-mandatory-advertisement-for-wake-on-lan
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-a-mandatory-advertisement-for-wake-on-lan.md
cmProducts: []
platformId: 3d26cdc2-560c-77c2-8b09-c719c69db0b8
---

# Configure a Mandatory Advertisement for Wake On LAN - Configuration Manager | Microsoft Learn

You can configure an existing mandatory advertisement for Wake On LAN by using the `SMS_Advertisement` class and properties.

### To configure a mandatory advertisement for Wake On LAN

1. Set up a connection to the SMS Provider.
2. Get the specific advertisement using the provided advertisement ID.
3. Replace the `AdvertFlags` property value with the value indicating Wake On LAN.
4. Save the advertisement with the new property

## Example

The following example method configures a software distribution mandatory advertisement for Wake On LAN.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub SetWOLOnAdvertisment(connection, existingAdvertisementID)

    ' Define a constant with the hexadecimal value for WAKE_ON_LAN_ENABLED.
    Const WAKE_ON_LAN_ENABLED = &H00400000
    Dim advertisementToModify
    ' Get the specific advertisement instance to modify.
    Set advertisementToModify = connection.Get("SMS_Advertisement.AdvertisementID='" & existingadvertisementID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Advertisement Name:            " & advertisementToModify.AdvertisementName
    Wscript.Echo "Advertisement Flags (integer): " & advertisementToModify.AdvertFlags

    ' Set the new property value.
    advertisementToModify.AdvertFlags = advertisementToModify.AdvertFlags OR WAKE_ON_LAN_ENABLED

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

public void SetWOLOnAdvertisment(WqlConnectionManager connection,
                                 string existingAdvertisementID)
{
    // Define a constant with the hexadecimal value for WAKE_ON_LAN_ENABLED.
    const Int32 WAKE_ON_LAN_ENABLED = 0x00400000;

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

        // Modify the AdvertFlags value to include the WAKE_ON_LAN_ENABLED value.
        advertisementToModify["AdvertFlags"].IntegerValue = advertisementToModify["AdvertFlags"].IntegerValue | WAKE_ON_LAN_ENABLED;

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
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingAdvertisementID` | - Managed: `String`- VBScript: `String` | The ID of the advertisment. |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).