---
layout: Conceptual
title: Modify Advertisement Properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-modify-advertisement-properties
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
description: In Configuration Manager, the following example shows how to modify an existing advertisement by using the SMS_Advertisement class and class properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c0106112-6d6a-2415-f418-54ed6f9c4638
document_version_independent_id: a0a81279-9f7f-5323-7c57-53ef45e9d413
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-modify-advertisement-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-modify-advertisement-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-modify-advertisement-properties.md
cmProducts: []
platformId: b31d8423-c673-4ace-9e9d-9995091263ee
---

# Modify Advertisement Properties - Configuration Manager | Microsoft Learn

The following example shows how to modify an existing advertisement, in Configuration Manager, by using the `SMS_Advertisement` class and class properties.

### To modify advertisement properties

1. Set up a connection to the SMS Provider.
2. Get the specific advertisement using an existing advertisement ID.
3. Replace the existing advertisement property (in this case, advertisement comment).
4. Save the new advertisement and properties.

## Example

The following example method modifies advertisement properties for software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ModifyAdvertisement(connection, existingAdvertisementID, newAdvertisementComment )
    Dim advertisementToModify
    ' Get the specific advertisement instance to modify.
    Set advertisementToModify = connection.Get("SMS_Advertisement.AdvertisementID='" & existingAdvertisementID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Advertisement Name: " & advertisementToModify.AdvertisementName
    Wscript.Echo "Comment:            " & advertisementToModify.Comment

    ' Set the new property value.
    advertisementToModify.Comment = newAdvertisementComment

    ' Save the advertisement.
    advertisementToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Values after change:  "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Advertisement Name: " & AdvertisementToModify.AdvertisementName
    Wscript.Echo "Comment:            " & AdvertisementToModify.Comment

End Sub
```

```c
public void ModifySWDAdvertisement(WqlConnectionManager connection, string existingAdvertisementID, string newAdvertisementComment)
{
    try
    {
        // Get the specific advertisement instance to modify.
        IResultObject advertisementToModify = connection.GetInstance(@"SMS_Advertisement.AdvertisementID='" + existingAdvertisementID + "'");

        // List the existing property values.
        Console.WriteLine();
        Console.WriteLine("Values before change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Advertisement Name: " + advertisementToModify["AdvertisementName"].StringValue);
        Console.WriteLine("Comment: " + advertisementToModify["Comment"].StringValue);

        // Set the new property value to  be modified.
        advertisementToModify["Comment"].StringValue = newAdvertisementComment;

        // Save the advertisement with the new value.
        advertisementToModify.Put();

        // Output the new property values.
        Console.WriteLine();
        Console.WriteLine("Values after change:");
        Console.WriteLine("____________________");
        Console.WriteLine("Advertisement Name: " + advertisementToModify["AdvertisementName"].StringValue);
        Console.WriteLine("Comment: " + newAdvertisementComment);
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
| `newAdvertisementComment` | - Managed: `String`- VBScript: `String` | The new comment for the advertisement. |

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