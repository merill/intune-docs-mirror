---
layout: Conceptual
title: Add an OS Install Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-install-package
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
description: Creates and populates an instance of SMS_OperatingSystemInstallPackage.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c1f28d43-4107-c1d2-1354-80578d122438
document_version_independent_id: 60f10d53-f5de-e868-6cf8-cbe8e597c4d8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-an-operating-system-install-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-an-operating-system-install-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-an-operating-system-install-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: f4c39e7a-4036-82b7-0575-8cd25e630ec6
---

# Add an OS Install Package - Configuration Manager | Microsoft Learn

You add an operating system install package to Configuration Manager by creating and populating an instance of [SMS_OperatingSystemInstallPackage](../reference/osd/sms_operatingsysteminstallpackage-server-wmi-class).

### To add an operating system install package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create an instance of [SMS_OperatingSystemInstallPackage](../reference/osd/sms_operatingsysteminstallpackage-server-wmi-class).
3. Set at least the *Name*, *PkgSourceFlag*, and *PkgSourcePath* properties.
4. Commit the changes.

## Example

The following example method adds an operating system install package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddOSInstallPackage(connection, name, description, path)

    Dim osInstallPackage

    Set osInstallPackage = connection.Get("SMS_OperatingSystemInstallPackage").SpawnInstance_()
    ' Populate the new package properties.
    osInstallPackage.Name = name
    osInstallPackage.Description = description

    osInstallPackage.PkgSourceFlag=2
    osInstallPackage.PkgSourcePath = path

    ' Write the package.
    osInstallPackage.Put_

End Sub
```

```c
public void AddOSInstallPackage(
    WqlConnectionManager connection,
    string name,
    string description,
    string path)
{
    try
    {
        // Create new operating system image package object.
        IResultObject osInstallPackage = connection.CreateInstance("SMS_OperatingSystemInstallPackage");

        // Populate operating system package properties.
        osInstallPackage["Name"].StringValue = name;
        osInstallPackage["Description"].StringValue = description;
        osInstallPackage["PkgSourceFlag"].IntegerValue = (int)PackageSourceFlag.StorageDirect;
        osInstallPackage["PkgSourcePath"].StringValue = path;

        // Save operating system package.
        osInstallPackage.Put();
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
| `name` | - Managed: `String`- VBScript: `String` | Name for the new operating system image package. |
| `description` | - Managed: `String`- VBScript: `String` | Description for the operating system image package. |
| `path` | - Managed: `Integer`- VBScript: `Integer` | Universal Naming Convention (UNC) path to the image Windows Image (WIM) file. |

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