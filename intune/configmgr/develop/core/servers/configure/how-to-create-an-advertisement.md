---
layout: Conceptual
title: Create a deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement
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
description: Examples of how to programmatically create a Configuration Manager deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8c27f060-15bf-53f6-c975-7e8bd93771b9
document_version_independent_id: d5c1b1dd-01d8-455f-83d8-d82eb2aaba04
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-an-advertisement
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement.md
cmProducts: []
platformId: 07391230-d0cb-1eb9-8365-f65c317e3dbe
---

# Create a deployment - Configuration Manager | Microsoft Learn

The following examples show how to create a Configuration Manager deployment with the [SMS_Advertisement](../../../reference/core/servers/configure/sms_advertisement-server-wmi-class) class and its properties.

Important

The account that creates the deployment needs the **Deploy Packages** permission for the collection and **Read** permission for the package.

## Overview

1. Set up a connection to the SMS Provider.
2. Create a new object of the `SMS_Advertisement` class.
3. Populate the new advertisement properties.
4. Save the new advertisement and properties.

## Examples

The following examples create an advertisement for software distribution.

For more information about calling the sample code, see [Calling Configuration Manager code snippets](../../understand/calling-code-snippets).

```vbs
Sub SWDCreateAdvertisement(connection, existingCollectionID, existingPackageID, existingProgramName, newAdvertisementName, newAdvertisementComment, newAdvertisementFlags, newRemoteClientFlags, newAdvertisementStartOfferDateTime, newAdvertisementStartOfferEnabled)
    Dim newAdvertisement
    ' Create the new advertisement object.
    Set newAdvertisement = connection.Get("SMS_Advertisement").SpawnInstance_

    ' Populate the advertisement properties.
    newAdvertisement.CollectionID = existingCollectionID
    newAdvertisement.PackageID = existingPackageID
    newAdvertisement.ProgramName = existingProgramName
    newAdvertisement.AdvertisementName = newAdvertisementName
    newAdvertisement.Comment = newAdvertisementComment
    newAdvertisement.AdvertFlags = newAdvertisementFlags
    newAdvertisement.RemoteClientFlags = newRemoteClientFlags
    newAdvertisement.PresentTime = newAdvertisementStartOfferDateTime
    newAdvertisement.PresentTimeEnabled = newAdvertisementStartOfferEnabled

    ' Save the new advertisement and properties.
    newAdvertisement.Put_

    ' Output new advertisement name.
    Wscript.Echo "Created advertisement: " & newAdvertisement.AdvertisementName

End Sub
```

```c
public void CreateSWDAdvertisement(WqlConnectionManager connection, string existingCollectionID, string existingPackageID, string existingProgramName, string newAdvertisementName, string newAdvertisementComment, int newAdvertisementFlags, int newRemoteClientFlags, string newAdvertisementStartOfferDateTime, bool newAdvertisementStartOfferEnabled)
{
    try
    {
        // Create new advertisement instance.
        IResultObject newAdvertisement = connection.CreateInstance("SMS_Advertisement");

        // Populate new advertisement values.
        newAdvertisement["CollectionID"].StringValue = existingCollectionID;
        newAdvertisement["PackageID"].StringValue = existingPackageID;
        newAdvertisement["ProgramName"].StringValue = existingProgramName;
        newAdvertisement["AdvertisementName"].StringValue = newAdvertisementName;
        newAdvertisement["Comment"].StringValue = newAdvertisementComment;
        newAdvertisement["AdvertFlags"].IntegerValue = newAdvertisementFlags;
        newAdvertisement["RemoteClientFlag"].IntegerValue = newRemoteClientFlags;
        newAdvertisement["PresentTime"].StringValue = newAdvertisementStartOfferDateTime;
        newAdvertisement["PresentTimeEnabled"].BooleanValue = newAdvertisementStartOfferEnabled;

        // Save the new advertisement and properties.
        newAdvertisement.Put();

        // Output new assignment name.
        Console.WriteLine("Created advertisement: " + newAdvertisement["AdvertisementName"].StringValue);
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
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/desktop/WmiSdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingCollectionID` | String | The ID of an existing collection with which to associate the advertisement. |
| `existingPackageID` | String | The ID of an existing package with which to associate the advertisement. |
| `existingProgramName` | String | The name for the program associated with the advertisement. |
| `newAdvertisementName` | String | The name for the new advertisement. |
| `newAdvertisementComment` | String | A comment for the new advertisement. |
| `newAdvertisementFlags` | Integer | Flags specifying options for the new advertisement. |
| `newRemoteClientFlags` | Integer | Flags specifying how the program should run when the client connects either locally or remotely to a distribution point. |
| `newAdvertisementStartOfferDateTime` | String | The time when the new advertisement is first offered. |
| `newAdvertisementStartOfferEnabled` | Boolean | `true` if the advertisement is offered. |

## Compiling the code

The C# example requires:

### Namespaces

- `System`
- `Microsoft.ConfigurationManagement.ManagementProvider`
- `Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine`

### Assembly

- `adminui.wqlqueryengine`
- `microsoft.configurationmanagement.managementprovider`
- `mscorlib`

## Robust programming

For more information about error handling, see [About Configuration Manager errors](../../understand/about-configuration-manager-errors).