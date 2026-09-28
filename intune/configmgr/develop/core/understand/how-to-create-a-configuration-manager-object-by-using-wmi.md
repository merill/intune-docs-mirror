---
layout: Conceptual
title: Create an Object by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi
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
description: Create a Configuration Manager object by calling the SWbemObject object SpawnInstance_ method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 85b6906d-d736-1c6c-d102-c9289f0c800a
document_version_independent_id: d186d046-b176-92f2-79d7-99adc7e0ec5c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e1ea8e9-94ec-62a5-54be-b33dc198fbb3
---

# Create an Object by Using WMI - Configuration Manager | Microsoft Learn

You create a Configuration Manager object, in Configuration Manager, by calling the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object [SpawnInstance_](/en-us/windows/win32/wmisdk/swbemobject-spawninstance-) method.

The [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) is the class definition for the object type that you want to create. For example, [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class). You get the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) by calling the [SWBemServices](/en-us/windows/win32/wmisdk/swbemservices) object [Get](/en-us/windows/win32/wmisdk/swbemservices-get) method.

### To create a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWBemServices](/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, call [Get](/en-us/windows/win32/wmisdk/swbemservices-get) to get the [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) for the Configuration Manager object class definition.
3. Call [SpawnInstance_](/en-us/windows/win32/wmisdk/swbemobject-spawninstance-) on the SWbemObject to create the new object. An SWbemObject is returned for the new object.
4. Using the SWbemObject returned from the call to SpawnInstance, populate the object properties.
5. Call [Put_](/en-us/windows/win32/wmisdk/swbemobject-put-) to commit the new object to the SMS Provider.

## Example

The following VBScript code example creates an [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class) object.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub CreatePackage (connection)

    On Error Resume Next

    ' Create a package object.
    Set package = connection.Get("SMS_Package").SpawnInstance_()

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't create packages object"
        Exit Sub
    End If

    ' Populate the object.
    package.Name = "Test Package"
    package.Description = "A test package"
    package.PkgSourceFlag = 2
    package.PkgSourcePath = "C:\temp"

    package.Put_

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't commit the package"
        Exit Sub
    End If

    WScript.Echo "Package created"
End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | [SWBemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code