---
layout: Conceptual
title: Perform an Asynchronous Query by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi
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
description: Learn how to perform a synchronous query for Configuration Manager objects and implement a sink method to handle query results.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ee6b134b-d8e4-b6da-5a80-11b4e30fd2e9
document_version_independent_id: 746144fe-1334-d025-dcf7-2d658a1bd3ff
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: b508e421-3a4f-62d0-a52b-1ac677b4e329
---

# Perform an Asynchronous Query by Using WMI - Configuration Manager | Microsoft Learn

In Configuration Manager, you perform a synchronous query for Configuration Manager objects by calling the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object [ExecQueryAsync](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execqueryasync) method and by implementing a sink method to handle query results.

To handle each returned object, create an [objWbemSink.OnObjectReady](/en-us/windows/win32/wmisdk/swbemsink-onobjectready) event subroutine. To be notified when the query is completed, create a [objWbemSink.OnCompleted](/en-us/windows/win32/wmisdk/swbemsink-oncompleted) event subroutine.

Note

Lazy properties are not returned in asynchronous queries. For more information, see [How to Read Lazy Properties by Using WMI](how-to-read-lazy-properties-by-using-wmi).

### To perform an asynchronous query

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Create an [OnObjectReady](/en-us/windows/win32/wmisdk/swbemsink-onobjectready) subroutine to handle objects by the query.
3. Create an [OnCompleted](/en-us/windows/win32/wmisdk/swbemsink-oncompleted) subroutine to handle query completion.
4. Using the [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, use [ExecQueryAsync](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execqueryasync) object to query Configuration Manager objects asynchronously.

## Example

The following VBScript code example asynchronously queries for all [SMS_Collection](../../reference/core/clients/collections/sms_collection-server-wmi-class) objects.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Dim bdone
Sub QueryCollection(connection)

    Dim sink
    bdone = False

    Set sink = WScript.CreateObject("wbemscripting.swbemsink","sink_")

    ' Query for all collections.
    connection.ExecQueryAsync sink, "select * from SMS_Collection"

    ' Wait until all instances are returned.
    While Not bdone
        wscript.sleep 1000
    Wend
 End Sub

' The sink subroutine to handle the OnObjectReady
' event. This is called as each object returns.
Sub sink_OnObjectReady(collection, octx)
    WScript.Echo "CollectionID: " + collection.CollectionID
    WScript.Echo "Name: " + collection.Name
    Wscript.Echo
End Sub

' The sink subroutine to handle the OnCompleted event.
' This is called when all the objects are returned.
' The oErr parameter obtains an SWbemLastError object,
' if available from the provider.
Sub sink_OnCompleted(HResult, oErr, oCtx)
    WScript.Echo "All collections returned"
    bdone = true
End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |