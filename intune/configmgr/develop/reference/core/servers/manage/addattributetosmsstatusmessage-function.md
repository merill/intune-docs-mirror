---
layout: Conceptual
title: AddAttributeToSMSStatusMessage Function - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/addattributetosmsstatusmessage-function
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
description: Learn to use AddAttributeToSMSStatusMessage to add a single optional status message attribute id-value pair to a status message object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 14c094a3-952a-77be-5b6a-008a5727585e
document_version_independent_id: 96d4b193-9750-bca4-2caa-24814eedc6b6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/addattributetosmsstatusmessage-function.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/addattributetosmsstatusmessage-function
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/addattributetosmsstatusmessage-function.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 5b97727d-7c7f-066d-1a86-e95c0f5dbe3c
---

# AddAttributeToSMSStatusMessage Function - Configuration Manager | Microsoft Learn

In Configuration Manager, the `AddAttributeToSMSStatusMessage` function adds a single optional status message attribute ID/value pair to a status message object.

## Syntax

```
[C/C++]
typedef DWORD (WINAPI *PROC_ADDATTRIBUTETOSMSSTATUSMESSAGE)
(
      HANDLE hStatusMessageObject,
      DWORD  dwAttributeID,
      LPCSTR pszAttributeValue
);
```

#### Parameters

`hStatusMessageObject` Data type: `HANDLE`

Qualifiers: [in]

Handle to the status message object.

`dwAttributeID` Data type: `DWORD`

Qualifiers: [in]

Status message attribute ID.

`pszAttributeValue` Data type: `LPCSTR`

Qualifiers: [in]

Status message attribute value.

## Return Values

One of the values in the following table.

| Value | Description |
| --- | --- |
| SMSSTATMSG\_SUCCESS | The attribute ID/value pair was successfully added to the object. |
| SMSSTATMSG\_OUT\_OF\_MEMORY | This function failed to allocate enough memory to add the attribute ID/value pair to the object. |
| STATMSG\_ERROR\_INVALID\_ATTR\_VALUE | The caller supplied `null` or a string that exceeded SMSSTATMSG\_MAX\_ATTR\_VALUE\_LENGTH characters in length for the `pszAttributeValue`parameter. |
| SMSSTATMSG\_ERROR\_MAX\_ATTR\_LIMIT | The object already has SMSSTATMSG\_MAX\_NUM\_ATTRS attribute ID/value pairs associated with it, which is the maximum permitted number. |
| SMSSTATMSG\_ERROR\_UNKNOWN | Encountered an unknown error while trying to add the attribute ID/value pair. |

## Remarks

Smscstat.h includes the following #define for calling `AddAttributeToSMSStatusMessage` by using the Win32 function `GetProcAddress`.

```
#define PROCNAME_ADDATTRIBUTETOSMSSTATUSMESSAGE "AddAttributeToSMSStatusMessage"
```

All Configuration Manager status messages include a set of mandatory properties, such as the name of the component that reported the message, the message ID, the time the message was reported, and the insertion strings for the message. These mandatory properties are initialized when the status message object is created and by the parameters passed into the status message reporting API functions. In addition to the mandatory properties, a status message has zero or more optional properties associated with it. In the Configuration Manager status system, these optional properties are called attribute ID/value pairs or simply attributes. In Status Message Viewer, these optional properties appear in the **Properties** box when you double-click a status message to open the **Status Message Details** box.

Attribute ID/value pairs are associated with status messages to facilitate the construction of efficient status message queries. For example, when any Configuration Manager component reports a status message related to a particular Configuration Manager package (a software distribution object), the status message includes the package ID as an attribute ID/value pair. The administrator can execute a query to retrieve all the status messages associated with the package. The status message tables in the Configuration Manager SQL Server database are indexed to allow messages to be retrieved efficiently by attribute ID/value pairs.

An attribute ID/value pair is composed of a `DWORD` type as the attribute ID and a null-terminated ASCII string as the attribute data. The possible attribute IDs are listed in the following table. These IDs currently specify all object identifiers for objects that are specific to Configuration Manager that are associated with the Configuration Manager software distribution features. Unless your application is integrating with the software distribution functionality, it is highly unlikely that you need to associate any attribute ID/value pairs with any of the status messages to report. Therefore, it is highly unlikely that you ever need to call this function from an application.

| Value | Description |
| --- | --- |
| SMSSTATMSG\_ATTR\_ID\_PACKAGE\_ID (400) | The attribute value is the eight-character ID of a Configuration Manager package. |
| SMSSTATMSG\_ATTR\_ID\_ADVERTISEMENT\_ID (401) | The attribute value is the eight-character ID of a Configuration Manager advertisement. |
| SMSSTATMSG\_ATTR\_ID\_COLLECTION\_ID (402) | The attribute value is the eight-character ID of a Configuration Manager collection. |
| SMSSTATMSG\_ATTR\_ID\_USER\_NAME (403) | The attribute value is a Windows NT user name and domain of the form domain\user name. In situations where the domain is not available, the attribute value takes the form of user name alone. |
| SMSSTATMSG\_ATTR\_ID\_DISTRIBUTION\_POINT (404) | The attribute value is a Configuration Manager NAL path for a Configuration Manager distribution point. |

## Requirements

Smscstat.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).