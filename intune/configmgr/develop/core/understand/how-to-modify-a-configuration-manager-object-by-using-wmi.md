---
layout: Conceptual
title: Modify an Object by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi
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
description: Learn how to modify an Object by using WMI.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 20dc2e1d-0a8f-1e7f-b268-45ed65480ad7
document_version_independent_id: 7e9e1e9f-317b-52bb-4073-772548d5c05e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0e906963-7330-b7c3-73a6-f00d8557757c
---

# Modify an Object by Using WMI - Configuration Manager | Microsoft Learn

You modify a Configuration Manager object, in Configuration Manager, by using the object's [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object to change its properties.

### To modify a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, call the [Get](/en-us/windows/win32/wmisdk/swbemservices-get) method and specify the class and key information for the object you want. This returns a [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) representing object.
3. Using the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject), update the object properties.
4. Call [Put_](/en-us/windows/win32/wmisdk/swbemobject-put-) to update the object in the SMS Provider.

## Example

The following VBScript code example gets a package (SMS\_Package) object, changes the package description, and then commits the changes back to the SMS Provider. In this example, the package is retrieved through a call to the SWbemServices object [Get](/en-us/windows/win32/wmisdk/swbemservices-get). You can also retrieve the package by using a query. For more information, see [How to Perform a Synchronous Configuration Manager Query by Using WMI](how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub ModifyPackageDescription (connection, packageID, description)

    On Error Resume Next
    Dim package

    ' Get the package.
    Set package = connection.Get("SMS_Package.PackageID='" & packageID & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get package " + packageID
        Exit Sub
    End If

    Wscript.Echo "Package Name: " + package.Name
    Wscript.Echo "Current Description: " + package.Description

    ' Update and commit the package.
    package.Description = description

    package.Put_
    If Err.Number<>0 Then
        WScript.Echo "Couldn't commit the package"
        Exit Sub
    End If

    Wscript.Echo "New Description: " + package.Description
End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `packageID` | `String` | The package identifier. This is available from the `SMS_Package` class `PackageID` identifier. |
| `Description` | `String` | A new description for the object. |