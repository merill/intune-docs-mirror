---
layout: Conceptual
title: CCM_UserLogonEvents Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_userlogonevents-client-wmi-class
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
description: A client class that represents a user logon event.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ba1c3e23-6686-c35f-afdd-44378bd0f5ab
document_version_independent_id: aed23a69-feee-cdec-d64c-98e0c6865815
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_userlogonevents-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_userlogonevents-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_userlogonevents-client-wmi-class.md
cmProducts: []
platformId: 76fa7506-1cb2-1db6-4354-09da3364661d
---

# CCM_UserLogonEvents Class - Configuration Manager | Microsoft Learn

The `CCM_UserLogonEvents` Client WMI class is a client class, in Configuration Manager, that represents a user logon event.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_UserLogonEvents
{
    UInt64 LogoffTime;
    UInt64 LogonTime;
    String UserSID;
};

```

## Methods

The `CCM_UserLogonEvents` class does not define any methods.

## Properties

`LogoffTime` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

The number of seconds elapsed since midnight (00:00:00), January 1, 1970, Coordinated Universal Time (UTC).

`LogonTime` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

The number of seconds elapsed since midnight (00:00:00), January 1, 1970, Coordinated Universal Time (UTC).

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The SID of the user.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).