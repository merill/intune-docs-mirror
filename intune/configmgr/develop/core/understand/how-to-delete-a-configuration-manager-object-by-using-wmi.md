---
layout: Conceptual
title: Delete an Object by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi
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
description: To delete a Configuration Manager object, call the SWbemObject object Delete_ method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a6743475-64da-ff84-f07b-2270402eb4f9
document_version_independent_id: a86c3bf8-b3bf-cec1-9983-ee7c12eddcaf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4fd851ae-e5ff-04bd-e4fd-612bf24a1da1
---

# Delete an Object by Using WMI - Configuration Manager | Microsoft Learn

To delete a Configuration Manager object, in Configuration Manager, call the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object [Delete_](/en-us/windows/win32/wmisdk/swbemobject-delete-) method.

### To delete a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, call the [Get](/en-us/windows/win32/wmisdk/swbemservices-get) method and specify the class and key information for the object you want to delete. `Get` returns a `SWbemObject` that represents the object.
3. Using the `SWbemObject`, call `Delete` to delete the object.

## Example

The following VBScript code example deletes the package ([SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class)) identified by its package identifier `packageID`.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub DeletePackage (connection, packageID)

    On Error Resume Next
    Dim package

    Set package = connection.Get("SMS_Package.PackageID='" & packageID & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get package " + packageID
        Exit Sub
    End If

    package.Delete_

    WScript.Echo "Package deleted"

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't delete " + packageID
        Exit Sub
    End If

End Sub

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | `SWbemServices` | A valid connection to the SMS Provider. |
| `packageID` | `String` | The package identifier. This is obtained from the `SMS_Package` class `PackageID`. |