---
layout: Conceptual
title: View the Properties for an OS Image - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Learn how to view an image file's properties in XML format using a Microsoft operating system's image package.
locale: en-us
document_id: e9822df4-6483-6156-79a5-f280ce9d3336
document_version_independent_id: 5a353936-f061-75e5-1876-69a04dd8306e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e99461b4-687d-3768-3ef5-1b05240a0b6b
---

# View the Properties for an OS Image - Configuration Manager | Microsoft Learn

In Configuration Manager, you view the image properties for the Windows Image (WIM) file that is contained in an operating system package by calling the [SMS_ImagePackage](../reference/osd/sms_imagepackage-server-wmi-class) class instance [GetImageProperties](../reference/osd/getimageproperties-method-in-class-sms_imagepackage) method.

The image properties are available in XML format.

### To view image properties

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the `SMS_ImagePackage` class instance that you want to update.
3. Call the [GetImageProperties](../reference/osd/getimageproperties-method-in-class-sms_imagepackage) class instance method.
4. Access property XML by using the *ImageProperty* parameter.

## Example

The following example displays the operating system image package property XML that defines the package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub ViewOSImage(connection,imagePackageID)

    Dim imagePackage
    Dim inParam
    Dim outParams

    ' Get the image.
    Set imagePackage = connection.Get("SMS_ImagePackage.PackageID='" & imagePackageID & "'")

    ' Obtain an InParameters object specific
    ' to the method.
    Set inParam = imagePackage.Methods_("GetImageProperties"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    inParam.Properties_.Item("SourceImagePath") =  imagePackage.PkgSourcePath

    ' Execute the method.
    Set outParams = connection.ExecMethod("SMS_ImagePackage", "GetImageProperties", inParam)

    ' Display the image properties XML.
    Wscript.echo "ImageProperty: " & outParams.ImageProperty

End Sub
```

```c
public void ViewOSImage(
    WqlConnectionManager connection,
    string imagePackageId)
{
    try
    {
        IResultObject imagePackage = connection.GetInstance(@"SMS_ImagePackage.PackageID='" + imagePackageId + "'");

        Dictionary<string, Object> inParams = new Dictionary<string, object>();

        inParams.Add("SourceImagePath", imagePackage["PkgSourcePath"].StringValue);
        IResultObject result = connection.ExecuteMethod("SMS_ImagePackage", "GetImageProperties", inParams);

        Console.WriteLine(result["ImageProperty"].StringValue);
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