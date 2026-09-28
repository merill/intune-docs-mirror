---
layout: Conceptual
title: Add an OS Image Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-image-package-in-configuration-manager
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
description: Add an operating system image package by creating an instance of the SMS_ImagePackage class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bcb853a2-5b58-9f25-0573-f5ff438bbec0
document_version_independent_id: 95244848-f339-7651-1fd0-56a12028a7a4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-an-operating-system-image-package-in-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-an-operating-system-image-package-in-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-an-operating-system-image-package-in-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1d8246b1-30ab-7767-fba3-d4c5e32407aa
---

# Add an OS Image Package - Configuration Manager | Microsoft Learn

In Configuration Manager, you add an operating system image package by creating an instance of [SMS_ImagePackage](../reference/osd/sms_imagepackage-server-wmi-class) class. The path to the Windows Image (WIM) file is specified in the **PkgSourcePath** property as a Universal Naming Convention (UNC) path.

### To create an operating system image package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create an instance of SMS\_ImagePackage.
3. Specify the path to the WIM file in **PkgSourcePath**.
4. Commit the SMS\_ImagePackage class instance.

## Example

The following example method creates an operating system package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddOSImagePackage(connection, newImagePackageName, newImagePackageDescription, newImagePackageSourcePath)

    Dim newImagePackage

    Set newImagePackage = connection.Get("SMS_ImagePackage").SpawnInstance_()
    ' Populate the new package properties.
    newImagePackage.Name = newImagePackageName
    newImagePackage.Description = newImagePackageDescription
    newImagePackage.PkgSourceFlag = 2
    newImagePackage.PkgSourcePath = newImagePackageSourcePath

    ' Save the package.
     newImagePackage.Put_

End Sub
```

```c
public void AddOSImagePackage(
    WqlConnectionManager connection,
    string newImagePackageName,
    string newImagePackageDescription,
    string newImagePackageSourcePath)
{
    try
    {
        // Create new package object.
        IResultObject newImagePackage = connection.CreateInstance("SMS_ImagePackage");

        // Populate new package properties.
        newImagePackage["Name"].StringValue = newImagePackageName;
        newImagePackage["Description"].StringValue = newImagePackageDescription;
        newImagePackage["PkgSourceFlag"].IntegerValue = (int)PackageSourceFlag.StorageDirect;
        newImagePackage["PkgSourcePath"].StringValue = newImagePackageSourcePath;

        // Save new package and new package properties.
        newImagePackage.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine();
        Console.WriteLine("Failed to create package. Error: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newImagePackageName` | - Managed: `String`- VBScript: `String` | The new image package name. |
| `newImagePackageDescription` | - Managed: `String`- VBScript: `String` | The new image package description |
| `newImagePackageSourcePath` | - Managed: `String`- VBScript: `String` | The UNC path to the WIM file. |

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