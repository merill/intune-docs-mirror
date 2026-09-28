---
layout: Conceptual
title: Use SMSCSTAT.DLL to Create Status Messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-using-smscstat.dll-to-create-status-messages
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
description: Smscstat.dll is a library of 32-bit C APIs for reporting Configuration Manager status messages from an application that is running on either client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 130e136a-6778-eccf-5907-59f5639bd502
document_version_independent_id: 15f62c1d-47d0-42dc-b2b0-712ee76ac439
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-using-smscstat.dll-to-create-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-using-smscstat.dll-to-create-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-using-smscstat.dll-to-create-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: 838d0bfc-1a17-e619-d31d-91a04258773f
---

# Use SMSCSTAT.DLL to Create Status Messages - Configuration Manager | Microsoft Learn

Smscstat.dll is a library of 32-bit C APIs for reporting Configuration Manager status messages from an application that is running on either client computer. Smscstat.dll is only present and only functions properly on Windows 95, Windows 98, Windows NT, Windows 2000, Windows Server 2003, Windows XP, and Windows Vista computers that have the client software installed on them.

## Loading Smscstat.dll

Applications need to explicitly load Smscstat.dll by using the Win32 **LoadLibrary()** API. **LoadLibrary** requires the full path to Smscstat.dll.

| Client | Path |
| --- | --- |
| SMS 2003 Advanced Client | %*windir*%\system32\ccm |
| Configuration Manager client | %*windir*%\system32\ccm |

The logic for finding the path on a given client is as follows:

1. Read the registry value Local SMS Path in key HKEY\_LOCAL\_MACHINE\Software\Microsoft\SMS\Client\Configuration\ClientProperties.
2. If last three characters of this path are **ccm**, then this is the Advanced Client or Configuration Manager client and Smscstat.dll resides in the path retrieved.

## Accessing the Functions in Smscstat.dll

When Smscstat.dll has been loaded, call the Win32 API `GetProcAddress()` to retrieve function pointers to the status message functions. The three status message functions are:

- `CreateSMSStatusMessage()`
- `AddAttributeToSMSStatusMessage()`
- `ReportSMSStatusMessage`

    `GetProcAddress()` returns a pointer of type `FARPROC`. For convenience, `Smscstat.h` (provided with the SMS 2003 SDK) defines C function prototypes for the status message APIs. The application should cast the pointer returned by`GetProcAddress()` to the appropriate prototype and then call the function through the pointer.

    If Smscstat.dll doesn't exist, as in the case of SMS 2.0 Legacy Clients that don't have Service Pack 1 or a later service pack installed, `LoadLibrary()` fails. A subsequent call to the Win32 API `GetLastError()` returns an error code indicating that the file doesn't exist. Most likely this will be error 126: "The specified module couldn't be found."

    The Win32 API `FreeLibrary` should be called when access to the functions is no longer need.

## Using the Status Message Functions in Smscstat.dll

There are three steps to using the status message functions.

1. Create a status message object by calling the `CreateSMSStatusMessage()` function. This function allocates an object and returns a handle to the caller.
2. Add any needed status message attributes to the object by using the `AddAttributeToSMSStatusMessage()` function. Status message attributes are optional and are required only if the application needs to integrate with a particular Configuration Manager feature. Most applications won't do this.
3. Call `ReportSMSStatusMessage` to submit the status message to the Configuration Manager status system and deallocate the object.