---
layout: Conceptual
title: About Component Status Messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-component-status-messages
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
description: The message text for both the Configuration Manager components and the raw user-defined messages is contained in message DLLs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: a6d96a89-ddad-0aa2-e20d-24a418d7fb81
document_version_independent_id: 6c1de077-8a49-97ec-95c6-295739aba868
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-configuration-manager-component-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-configuration-manager-component-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-configuration-manager-component-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 1e8491e5-2d54-c88d-344f-9b4a2d75e576
---

# About Component Status Messages - Configuration Manager | Microsoft Learn

The message text for both the Configuration Manager components and the raw user-defined messages is contained in message DLLs. The [SMS_StatMsgInsStrings Server WMI Class](../../../reference/core/servers/manage/sms_statmsginsstrings-server-wmi-class) class contains the insertion strings for those messages that use insertion strings. To read the SMS component and raw user-defined messages, you must know the message DLL that contains the message text.

Note

If the status message is in Srvmsgs.dll, Provmsgs.dll, or Climmsgs.dll, you can use [FormatModuleMessage Method](../../../reference/core/servers/manage/formatmodulemessage-method) to resolve the message.

You can get the DLL name from the [SMS_StatMsgModuleNames Server WMI Class](../../../reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class). The [SMS_StatMsgModuleNames Server WMI Class](../../../reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class) class contains the **ModuleName** and **MsgDLLName** properties. You can use **ModuleName** to join the `SMS_StatMsgModuleNames` class with the `SMS_StatusMessage` class, as the following example shows.

```
// Note that this query returns all the instances found in the SMS_Status_Message
// class. This query can return several thousand instances. If you test this
// query, you should add a where clause to limit its scope, or set the
// InstanceCount context qualifier to limit the number of instances returned.
SELECT B.Severity, B.MessageID, B.MessageType,
       B.Win32Error, B.SiteCode, B.MachineName,
       B.Component, C.MsgDLLName, D.InsStrValue
FROM SMS_StatusMessage AS B
     INNER JOIN SMS_StatMsgModuleNames AS C
     ON B.ModuleName = C.ModuleName
     LEFT OUTER JOIN SMS_StatMsgInsStrings AS D
     ON B.RecordID = D.RecordID
ORDER BY B.Sitecode, B.RecordID, B.MessageID, D.InsStrIndex
```

You can use the **MessageID** and **Component** names from the list to limit your status message query. For example, you can add a WHERE clause to limit the status messages to the SMS\_Distribution\_Manager component.

After you have the DLL name, you can use the Microsoft Win32 API function **FormatMessage** to retrieve the message text from the component's message DLL. This requires you to get the module handle for the DLL by using the Win32 API function **GetModuleHandle**. The *dwMessageId* parameter is the OR'd result of the **MessageID** and the **Severity** properties. You should set the FORMAT\_MESSAGE\_ARGUMENT\_ARRAY flag and pass the insertion strings as an array.

The following code shows how to call **FormatMessage** to retrieve the message text from a DLL.

```
// Get the module handle for the component's message DLL. This assumes the
// message DLL is loaded. If the DLL is not loaded, then load the DLL by using
// the Win32 API LoadLibrary.
hmodMessageDLL = GetModuleHandle(MsgDLLName);

// The flags tell FormatMessage to allocate the memory needed for the message,
// to get the message text from a message DLL, and that the insertion strings are
// stored in an array, instead of a variable length argument list. The last
// parameter, apInsertStrings, is the array of insertion strings returned by the
// query.
dwMsgLen = FormatMessage(FORMAT_MESSAGE_ALLOCATE_BUFFER |
                         FORMAT_MESSAGE_FROM_HMODULE |
                         FORMAT_MESSAGE_ARGUMENT_ARRAY,
                         hmodMessageDLL,
                         Severity | MessageID,
                         0,
                         lpBuffer,
                         nSize,
                         apInsertStrings);

// Free the memory after you use the message text.
LocalFree(lpBuffer);
```