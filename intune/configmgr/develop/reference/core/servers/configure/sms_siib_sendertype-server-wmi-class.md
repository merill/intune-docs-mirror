---
layout: Conceptual
title: SMS_SIIB_SenderType Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_sendertype-server-wmi-class
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
description: Article outlining the use of SMS_SIIB_SenderType in Configuration Manager to represent the sender type in Configuration Manager property pages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a4f409e6-7d64-5e66-6f4f-6b18691ead0a
document_version_independent_id: d96afa8a-d48b-9ec1-9e6a-a2223785939d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siib_sendertype-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siib_sendertype-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siib_sendertype-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 136ae9b0-9530-bad8-a6cb-c3420999390f
---

# SMS_SIIB_SenderType Class - Configuration Manager | Microsoft Learn

The `SMS_SIIB_SenderType` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the sender type for the associated Configuration Manager console property pages.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_SenderType : SMS_SiteInstallItemBase
{
   String ChmFile;
   UInt32 DescriptionID;
   UInt32 DispIconID;
   UInt32 DispNameID;
   UInt32 Flags;
   String GUID;
   String HtmFile;
   String ItemName;
   String ItemType;
   String ResDLL;
   String SenderType;
   String SiteCode;
   String Units[];
};
```

## Methods

The `SMS_SIIB_SenderType` class does not define any methods.

## Properties

`ChmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

Compressed .chm file containing the .htm file for the sender type.

`DescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the description.

`DispIconID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the display icon.

`DispNameID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the display name.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: [bits]

Flags defining operations supported by the sender. Possible values are:

0 ALLOW\_ADD

1 ALLOW\_DELETE

2 ALLOW\_MODIFY

`GUID` Data type: `String`

Access type: Read-only

Qualifiers: None

GUID representing the Microsoft Management Console node for the property page.

`HtmFile` Data type: `String`

Access type: Read-only

Help file (.htm) for the sender type.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`ResDLL` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the resource DLL containing the resource strings for `DescriptionID`, `DispIconID`, and `DispNameID`.

`SenderType` Data type: `String`

Access type: Read-only

Qualifiers: None

Sender service name.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

`Units` Data type: `String` Array

Access type: Read-only

Qualifiers: None

See [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).