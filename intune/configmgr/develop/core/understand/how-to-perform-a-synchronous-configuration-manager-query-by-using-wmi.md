---
layout: Conceptual
title: Perform a Synchronous Query by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi
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
description: In Configuration Manager, you perform a synchronous query for Configuration Manager objects by calling the SWbemServices object ExecQuery method and passing a WQL query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 03473e77-3a2d-0bc6-2c4c-c8f630f34bfb
document_version_independent_id: 88700bf7-0e77-5b55-d860-434042e8679e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 9bb44457-aae9-23d8-1acb-66a272d67c94
---

# Perform a Synchronous Query by Using WMI - Configuration Manager | Microsoft Learn

In Configuration Manager, you perform a synchronous query for Configuration Manager objects by calling the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object [ExecQuery](/en-us/windows/win32/wmisdk/swbemservices-execquery) method and passing a WQL query.

A synchronous query is a query that maintains control over the process of your application for the duration of the query. A synchronous query has the potential of locking up your application for large queries or for queries over a network. Alternatively, you can run an asynchronous query that returns control to the application while the query is run. For more information, see [How to Perform an Asynchronous Configuration Manager Query by Using Managed Code](how-to-perform-an-asynchronous-query-by-using-managed-code)

Note

Lazy properties are not returned in synchronous queries. For more information, see [How to Read Lazy Properties by Using WMI](how-to-read-lazy-properties-by-using-wmi).

### To perform a synchronous query

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the SWbemServices object that you obtain from step one, use the ExecQuery method to get a [SWbemObjectSet](/en-us/windows/win32/wmisdk/swbemobjectset) collection containing the query results.
3. Iterate through the SWbemObjectSet collection to access a [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) for each object returned by the query.

## Example

The following example performs a synchronous query of all packages in Configuration Manager.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Sub QueryPackages(connection)

    On Error Resume next

    Dim packages
    Dim package

    ' Run the query.
    Set packages = _
        connection.ExecQuery("Select * From SMS_Package")

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get Packages"
        Wscript.Quit
    End If

    For Each package In packages
        WScript.Echo  package.Name
    Next

    If packages.Count=0 Then
        Wscript.Echo "No packages found"
    End If

End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |