---
layout: Conceptual
title: Assign an Advertisement to a Collection of Computers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-assign-an-advertisement-to-a-collection-of-computers
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
description: Learn how to use the SMS_Advertisement class to assign an advertisement to a collection of computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ffb4657b-bf46-c6d8-a1ca-9aa6ddae7ef8
document_version_independent_id: 5c45de8c-4d2d-220e-757a-a80a8fdd0ac4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-assign-an-advertisement-to-a-collection-of-computers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-assign-an-advertisement-to-a-collection-of-computers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-assign-an-advertisement-to-a-collection-of-computers.md
cmProducts: []
platformId: fe229750-fed3-7084-11c2-207ed167e58d
---

# Assign an Advertisement to a Collection of Computers - Configuration Manager | Microsoft Learn

You can assign an advertisement to a collection by using the `SMS_Advertisement` class in Configuration Manager. Advertisements are closely tied to packages, programs and collections. For more information, see [Software Distribution Overview](software-distribution-overview).

Note

Detailed information about the `SMS_Advertisement` class and class properties is in the reference section of the Configuration Manager Software Development Kit (SDK).

### To assign an advertisement to a collection

1. Set up a connection to the SMS Provider.
2. Get the specific advertisement using the existing advertisement ID.
3. Populate the advertisement collection ID property with the existing collection ID.
4. Save the advertisement and properties.

## Example

The following example method assigns a specific advertisement to a collection for use in software distribution.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub SWDAssignAdvertisementCollection(connection, existingAdvertisementID, existingCollectionID)

    ' Get the specific advertisement object.
    Set advertisementToAssign = connection.Get("SMS_Advertisement.AdvertisementID='" & existingAdvertisementID & "'")

    ' Fill the advertisement properties for collection.
    advertisementToAssign.CollectionID = existingCollectionID

    ' Save the advertisement.
    advertisementToAssign.Put_

    ' Output advertisement and collection information.
    Wscript.Echo "Assigned advertisement: " & existingAdvertisementID
    Wscript.Echo "                        " & advertisementToAssign.AdvertisementName
    Wscript.Echo "To collection:          " & advertisementToAssign.CollectionID

End Sub
```

```c
public void AssignSWDAdvertisementToCollection(WqlConnectionManager connection, string existingAdvertisementID, string existingCollectionID)
{
    try
    {
        // Get specific advertisement instance (using the passed in value existingAdvertisementID).
        IResultObject advertisementToAssign = connection.GetInstance(@"SMS_Advertisement.AdvertisementID='" + existingAdvertisementID + "'");

        // Populate the collection id property of the advertisement.
        advertisementToAssign["CollectionID"].StringValue = existingCollectionID;

        // Save the advertisement and properties.
        advertisementToAssign.Put();

        // Output advertisement and collection information.
        Console.WriteLine("Assigned advertisement: " + existingAdvertisementID);
        Console.WriteLine("                        " + advertisementToAssign["AdvertisementName"].StringValue);
        Console.WriteLine("To collection:          " + existingCollectionID);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to assign advertisement. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingAdvertisementID` | - Managed: `String`- VBScript: `String` | The ID of an existing advertisement. |
| `existingCollectionID` | - Managed: `String`- VBScript: `String` | The ID of an existing collection. |

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