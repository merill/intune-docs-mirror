---
layout: Conceptual
title: Add a Boot Image from a WIM File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-boot-image-from-a-wim-file
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
description: You add a boot image from a Windows Image (WIM) file to Configuration Manager by creating an instance of SMS_BootImagePackage.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3280eb85-eb79-4a05-a110-7a1ecb61b49c
document_version_independent_id: bee3ea29-abcc-1112-4b80-fd13ab00a07c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-a-boot-image-from-a-wim-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-a-boot-image-from-a-wim-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-a-boot-image-from-a-wim-file.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4e72df29-97a2-c636-597b-400c0bce37f2
---

# Add a Boot Image from a WIM File - Configuration Manager | Microsoft Learn

You add a boot image from a Windows Image (WIM) file to Configuration Manager by creating an instance of [SMS_BootImagePackage](../reference/osd/sms_bootimagepackage-server-wmi-class). The property ImagePath must be set to the Universal Naming Convention (UNC) path to the WIM file. The property ImageIndex is the index to the required image within the WIM file.

If the boot image requires Windows drivers, you specify them in the `ReferencedDrivers` property, which is an array of [SMS_Driver_Details](../reference/osd/sms_driver_details-server-wmi-class).

Note

When the boot image is updated, for example, when a Configuration Manager binary or boot image property is changed, the boot image must be updated by calling the [SMS_BootImagePackage](../reference/osd/sms_bootimagepackage-server-wmi-class) class [RefreshPkgSource](../reference/osd/refreshpkgsource-method-in-class-sms_bootimagepackage) method.

### To add a boot image from a WIM file

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create an instance of SMS\_BootImagePackage.
3. Set at least the Name, ImagePath, and ImageIndex properties.
4. Commit the changes.

## Example

The following example method adds a boot image from a WIM file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddBootImagePackage(connection, name, description, pathToWim)

    Dim bootImagePackage

    Set bootImagePackage = connection.Get("SMS_BootImagePackage").SpawnInstance_()
    ' Populate the new package properties.
    bootImagePackage.Name = name
    bootImagePackage.Description = description

    bootImagePackage.ImagePath = pathToWim  'UNC path to WIM file.
    bootImagePackage.ImageIndex = 1 ' Index into WIM file for image

    bootImagePackage.Put_

End Sub
```

```c
public void AddBootImage(
    WqlConnectionManager connection,
    string name,
    string description,
    string pathToWim)
{
    try
    {
        // Create new boot image package object.
        IResultObject bootImagePackage = connection.CreateInstance("SMS_BootImagePackage");

        // Populate new boot image package properties.
        bootImagePackage["Name"].StringValue = name;
        bootImagePackage["Description"].StringValue = description;
        bootImagePackage["ImagePath"].StringValue = pathToWim; // UNC path required.
        bootImagePackage["ImageIndex"].IntegerValue = 1; // Index into WIM file for image.

        // Save new package and new package properties.
        bootImagePackage.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine();
        Console.WriteLine("Failed to create package. Error: " + e.Message);
        throw;
    }
}
```

The sample method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `name` | - Managed: `String`- VBScript: `String` | Name for the new boot image package. |
| `description` | - Managed: `String`- VBScript: `String` | Description for the boot image package. |
| `pathToWIM` | - Managed: `Integer`- VBScript: `Integer` | UNC path to the image. |

## Compiling the Code

The C# example has the following compilation requirements:

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