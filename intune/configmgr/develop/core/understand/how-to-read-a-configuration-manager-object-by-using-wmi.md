---
layout: Conceptual
title: Read an Object by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi
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
description: In Configuration Manager, you read a Configuration Manager object by using the SWbemServices object Get method to return an object instance that is identified by a key value.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 50756aca-6191-a1de-e823-49b136a0915f
document_version_independent_id: fc94392b-e928-2e02-0e0f-5c35a105f5b3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2c6fcd20-ff31-6df3-1835-28081889d458
---

# Read an Object by Using WMI - Configuration Manager | Microsoft Learn

In Configuration Manager, you read a Configuration Manager object by using the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object [Get](/en-us/windows/win32/wmisdk/swbemservices-get) method to return an object instance that is identified by a key value.

Note

To query for multiple objects, use either a synchronous or asynchronous query. For more information, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code)

### To read a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the SWbemServices object that you obtain from step 1, call the Get method and specify the class and key information for the object you want.

## Example

The following VBScript code example function displays the name and description for a supplied key package identifier (`packageID`).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub DisplayPackageName (connection, packageID)

    On Error Resume Next
    Dim package

    Set package = connection.Get("SMS_Package.PackageID='" & packageID & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get package " + packageID
        Exit Sub
    End If

    Wscript.Echo "Package Name: " + package.Name
    Wscript.Echo "Package Description: " + package.Description

End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `packageID` | `String` | A package identifier. This can be obtained from the [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class) class PackageID property. |