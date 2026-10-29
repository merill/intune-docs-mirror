---
layout: Conceptual
title: SMS_SiteInstallItemBase Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class
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
description: An SMS Provider server class that represents the abstract base class from which all specific site install item configuration classes are derived.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4d8e8289-27c0-7b1f-3f84-09b825b45b63
document_version_independent_id: bb367613-1e02-7f29-9c09-fd572dca8b7a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5ced5e9c-0a1e-9c46-2053-8e4e9a700619
---

# SMS_SiteInstallItemBase Class - Configuration Manager | Microsoft Learn

The `SMS_SiteInstallItemBase` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the abstract base class from which all specific site install item configuration classes are derived.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteInstallItemBase : SMS_SiteInstallItem
{
     String ItemName;
     String ItemType;
     String Units[];
     String SiteCode;
};
```

## Methods

The `SMS_SiteInstallItemBase` class does not define any methods.

## Properties

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItem Server WMI Class](sms_siteinstallitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItem Server WMI Class](sms_siteinstallitem-server-wmi-class).

`Units` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Units to install. Possible values are:

- SMS
- ADMIN\_UI
- Remote control

    `SiteCode` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    For internal use only.

## Remarks

Class qualifiers for this class include:

- Abstract
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Use classes derived from [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class) to view the install map represented by [SMS_SiteInstallMap Server WMI Class](sms_siteinstallmap-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).