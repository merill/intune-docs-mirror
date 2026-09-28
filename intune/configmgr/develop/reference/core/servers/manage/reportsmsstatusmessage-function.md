---
layout: Conceptual
title: ReportSMSStatusMessage Function - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/reportsmsstatusmessage-function
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
description: The ReportSMSStatusMessage function submits a status message object to the Configuration Manager status system and then deallocates the object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fe21d8ff-e3b6-bcca-5504-8eddc64f1424
document_version_independent_id: 901958fe-241b-fc73-6a1e-48ae9608ea4d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/reportsmsstatusmessage-function.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/reportsmsstatusmessage-function
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/reportsmsstatusmessage-function.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: f0644044-3740-b36a-65d0-c73ecb809fa2
---

# ReportSMSStatusMessage Function - Configuration Manager | Microsoft Learn

The `ReportSMSStatusMessage` function, in Configuration Manager, submits a status message object to the Configuration Manager status system and then deallocates the object.

## Syntax

```
[C/C++]
typedef DWORD (WINAPI *PROC_REPORTSMSSTATUSMESSAGE)
(
      HANDLE hStatusMessageObject,
      LPCSTR pszComponentName,
      LPCSTR pszSiteCode,
      LPCSTR pszTopLevelSiteCode
);
```

#### Parameters

`hStatusMessageObject` Data type: `HANDLE`

Qualifiers: [in, out]

Handle to the status message object. On input, supply the handle retrieved by [CreateSMSStatusMessage](createsmsstatusmessage-function). On successful return from the function, this parameter contains the handle to the deallocated object.

The behavior of this function is undefined for invalid handles and throws an access violation exception. Therefore, ensure that you supply a valid handle for this parameter. See Remarks.

`pszComponentName` Data type: `LPCSTR`

Qualifiers: [in]

Pointer to the name of the component reporting the status message. This name is a null-terminated ASCII component name. It appears in Status Message Viewer in the Component column and in Windows NT Event Viewer in the Category column. For more information , see the Remarks section later in this topic.

`pszSiteCode` Data type: `LPCSTR`

Qualifiers: [in]

Pointer to the Configuration Manager site code for the site to which to report the status message. The code is a null-terminated ASCII code that is exactly three characters long. Alternatively you can set this parameter to `null`. For more information, see the Remarks section later in this topic.

`pszTopLevelSiteCode` Data type: `LPCSTR`

Qualifiers: [in]

Pointer to the Configuration Manager site code for the highest site in the hierarchy to which the message can be replicated. The code is a null-terminated ASCII code. Alternatively, you can set this parameter to `null`. For more information, see the Remarks section later in this topic.

## Return Values

This function returns one of the values in the following table.

| Value | Description |
| --- | --- |
| SMSSTATMSG\_SUCCESS | The object was successfully submitted to the Configuration Manager status system. |
| SMSSTATMSG\_OUT\_OF\_MEMORY | This function failed to allocate enough memory to submit the object to the Configuration Manager status system. |
| SMSSTATMSG\_ERROR\_INVALID\_COMPONENT\_NAME | The caller supplied `null` or a string that exceeded SMSSTATMSG\_MAX\_COMPONENT\_NAME\_LENGTH characters in length for the `pszComponentName` parameter. |
| SMSSTATMSG\_ERROR\_INVALID\_SITE\_CODE | The caller supplied a non-NULL invalid string for `pszSiteCode`. |
| SMSSTATMSG\_ERROR\_UNKNOWN | The function encountered an unknown error while trying to submit the object to the Configuration Manager status system. |
| SMSSTATMSG\_ERROR\_INVALID\_TOP\_LEVEL\_SC | The caller supplied a non-NULL invalid string for `pszTopLevelSiteCode`. |
| SMSSTATMSG\_ERROR\_NOT\_SMS\_CLIENT | This function failed to submit the object to the Configuration Manager status system because the Configuration Manager client software is not properly installed on this computer. |

## Remarks

Smscstat.h includes the following #define for calling `ReportSMSStatusMessage` by using the Win32 function `GetProcAddress`.

```
#define PROCNAME_REPORTSMSSTATUSMESSAGE "ReportSMSStatusMessage"
```

When calling this function, use the `hStatusMessageObject` parameter to supply a handle for the status message to report. When this function returns, the retrieved object is guaranteed to be deallocated, regardless of the success of the function. If the function is unsuccessful and you want your application to try again, create a new status message before calling `ReportSMSStatusMessage`.

Use the `pszComponentName` parameter of this function to supply a name for the component that is reporting the status message. This name is not localizable to other languages, because the Configuration Manager administrator creates queries and filter rules that are based on the component name. This assists the administrator in quickly retrieving your particular status messages and in configuring Configuration Manager to handle these status messages in special ways.

In the `pszSiteCode` parameter, supply the code for the Configuration Manager site to which to submit the message. The code must be for one of the sites to which the Configuration Manager client currently belongs. Generally, you should supply `null` for this parameter, to indicate that the status message should be reported to all Configuration Manager sites to which the Configuration Manager client belongs.

The status system stops replication at the site indicated by `pszTopLevelSiteCode` no matter how the administrator has configured the replication rules. Generally, you should specify `null` for this parameter, to indicate that there is no top-level site code and that the message is free to replicate all the way to the top of the hierarchy. However, if there is a reason to prevent the replication past a certain site, you can supply the site code of that site using the `pszTopLevelSiteCode` parameter.

## Requirements

Smscstat.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).