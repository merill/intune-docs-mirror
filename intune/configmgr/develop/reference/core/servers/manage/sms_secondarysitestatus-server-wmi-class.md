---
layout: Conceptual
title: SMS_SecondarySiteStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_secondarysitestatus-server-wmi-class
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
description: The SMS_SecondarySiteStatus WMI class is an SMS Provider server class, in Configuration Manager, that represents secondary site installation or uninstallation status.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6c15abbe-8a04-d790-d5d5-ed835b48a67e
document_version_independent_id: 31e372d3-4791-ab69-7d53-db4c824fe5eb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_secondarysitestatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_secondarysitestatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_secondarysitestatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 242252d1-78d2-2be0-e4c3-edab0d658f7a
---

# SMS_SecondarySiteStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SecondarySiteStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents secondary site installation or uninstallation status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SecondarySiteStatus : SMS_BaseClass
{
    String Description;
    DateTime MessageTime;
    String SiteCode;
    UInt32 SiteInstallID;
    String Status;
    UInt32 StatusID;
};
```

## Methods

The `SMS_SecondarySiteStatus` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read

Qualifiers: none

Description of the status for secondary installation or uninstallation status.

`MessageTime` Data type: `DateTime`

Access type: Read

Qualifiers: [key]

Time of the message reported for the secondary site installation or uninstallation.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key]

Site code of the secondary site.

`SiteInstallID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

Site installation or uninstallation identifier.

`Status` Data type: `String`

Access type: Read

Qualifiers: none

Secondary site installation or uninstallation status.

`StatusID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

Identifier for the status.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).