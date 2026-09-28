---
layout: Conceptual
title: SMS_CIContentPackage Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_cicontentpackage-server-wmi-class
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
description: The SMS_CIContentPackage WMI class represents the relationship between configuration item and associated content to SMS Package where the binary content is packaged and distributed.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 66b2df1f-3a70-62af-ee0f-bbed8f2c388f
document_version_independent_id: 158a4d3d-7bf4-0bdc-dc3e-c28d95be96cd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_cicontentpackage-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_cicontentpackage-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_cicontentpackage-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 88a1cc33-5aa3-823d-0488-ddccdfd22998
---

# SMS_CIContentPackage Class - Configuration Manager | Microsoft Learn

The `SMS_CIContentPackage` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, represents the relationship between configuration item and associated content to `SMS Package` where the binary content is packaged and distributed.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIContentPackage : SMS_BaseClass
{
    UInt32 CI_ID;
    UInt32 CI_SecuredTypeID;
    String CI_UniqueID;
    String ModelName;
    String PackageID;
};
```

## Methods

The `SMS_CIContentPackage` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`CI_SecuredTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

CI\_SecuredTypeID is the associated RBAC security object type, depending on which object content (Application, Software Update and so on) is part of this package.

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

[SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).