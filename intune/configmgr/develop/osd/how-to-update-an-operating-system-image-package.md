---
layout: Conceptual
title: Update an OS Image Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package
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
description: Update an operating system using a Windows Image file that is associated with the operating system package in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 95d9abeb-90f3-a384-b288-280107758b63
document_version_independent_id: e0d0ca67-5fc7-e68c-c7d8-78f66a396473
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-update-an-operating-system-image-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 78bce71b-9f41-aba0-acbf-0a1dc2601529
---

# Update an OS Image Package - Configuration Manager | Microsoft Learn

In Configuration Manager, you update the Windows Image (WIM) file that is associated with the operating system package by calling the image package's [SMS_ImagePackage](../reference/osd/sms_imagepackage-server-wmi-class) class instance [ReloadImageProperties](../reference/osd/reloadimageproperties-method-in-class-sms_imagepackage) method. The image is updated based on the location defined in the `pkgSourcePath` property.

### To update an operating system image package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the `SMS_ImagePackage` class instance you want to update.
3. Call the `ReloadImageProperties` class instance method.
4. Commit the `SMS_ImagePackage` class instance.

## Example

The following example updates an operating system image package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub UpdateOSImage(connection,imagePackageID, sourcePath)

    Dim imagePackage

    ' Get the image.
    set imagePackage = connection.Get("SMS_ImagePackage.PackageID='" & imagePackageID & "'")

    ' Update the source.
    imagePackage.PkgSourcePath=sourcePath
    imagePackage.Put_
    imagePackage.RefreshPkgSource

End Sub
```

```c
public void UpdateOSImage(
    WqlConnectionManager connection,
    string imagePackageId,
    string sourcePath)
{
    try
    {
        // Get the image package.
        IResultObject imagePackage = connection.GetInstance(@"SMS_ImagePackage.PackageID='" + imagePackageId + "'");

        // Update the location.
        imagePackage["PkgSourcePath"].StringValue = sourcePath;
        imagePackage.Put();
        imagePackage.ExecuteMethod("RefreshPkgSource", null);
    }
    catch (SmsException e)
    {
        Console.WriteLine(e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `imagePackageID` | - Managed: `String`- VBScript: `String` | The package image identifier. It is available from `SMS_ImagePackage. PackageID`. |
| `sourcePath` | - Managed: `String`- VBScript: `String` | The path to the image package source in Universal Naming Convention (UNC) format. |

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