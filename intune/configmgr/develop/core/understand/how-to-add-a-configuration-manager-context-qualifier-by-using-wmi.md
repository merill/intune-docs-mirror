---
layout: Conceptual
title: Add a Context Qualifier by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi
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
description: Add context qualifiers to a connection (SWbemServices) or object (SWbemObject) by creating a SWbemNamedValueSet value set to hold the context qualifiers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: eea3745b-bd66-5089-1822-13d8729d0668
document_version_independent_id: ff29dc8b-f04e-47de-8372-167097293f66
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e0e3007d-0bdb-d409-db08-791e06a9ef00
---

# Add a Context Qualifier by Using WMI - Configuration Manager | Microsoft Learn

In Configuration Manager, you add context qualifiers to a connection ([SWbemServices](/en-us/windows/win32/wmisdk/swbemservices)) or object ([SWbemObject](/en-us/windows/win32/wmisdk/swbemobject)) by creating a [SWbemNamedValueSet](/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set to hold the context qualifiers. You then provide the [SWbemNamedValueSet](/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set as a parameter to connection and object methods.

in Configuration Manager, you can provide your application name (ApplicationName), computer name (MachineName) and locale identifier (LocaleID).

In most cases, context qualifiers are not required. The main exception is accessing the site control file where they are needed to set up session information. For more information, see [About the Configuration Manager Site Control File](about-the-configuration-manager-site-control-file).

### To add a Configuration Manager context qualifier

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Create a [WbemScripting.SWbemNamedValueSet](/en-us/windows/win32/wmisdk/swbemnamedvalueset) object and add the desired context qualifiers.
3. Use the [SWbemNamedValue](/en-us/windows/win32/wmisdk/swbemnamedvalue) value set you created in step two to pass context qualifiers to connection and object manipulation calls.

## Example

The following VBScript example creates a [SWbemNamedValueSet](/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set and adds the supplied context qualifiers. The following code example demonstrates how to call the method for use in an [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class) package object **Put** method call. For more information about Configuration Manager objects, see [Objects overview](configuration-manager-objects-overview).

`Dim context`

`Set context = CreateContextQualifiers("My application" , "My Computer" , "MS\1033")`

`package.Put_ , context`

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs

Function CreateContextQualifiers(applicationName, machineName, localeID)
    On Error Resume next
    Dim smsContext

    set smsContext = CreateObject("WbemScripting.SWbemNamedValueSet")

    ' Add the context qualifiers to the set.
    smsContext.Add "LocaleID", localeID
    smsContext.Add "MachineName", machineName
    smsContext.Add "ApplicationName", applicationName

    Set CreateContextQualifiers = smsContext

      If Err.Number<>0 Then
        WScript.Echo Err.Description
        CreateContextQualifiers = null
        Exit Function
    End If
End Function
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `applicationName` | - `String` | The ApplicationName context qualifier. |
| `machineName` | - `String` | The computer name qualifier. |
| `localeID` | - `String` | The locale identifier. For example, MS\1033 is English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property. |

## Compiling the Code

This VBScript example requires:

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../servers/configure/role-based-administration).