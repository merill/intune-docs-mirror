---
layout: Conceptual
title: SMS_ADDomain Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_addomain-server-wmi-class
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
description: Learn how to use the SMS_ADDomain class which contains Active Directory domains discovered by Configuration Manager Forest Discovery.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b33c8b20-447e-f18a-d10c-3af91b0a66f9
document_version_independent_id: 9939b767-26a0-82b1-f990-0230e73e7bc4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_addomain-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_addomain-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_addomain-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6b2795dc-8878-6765-aadb-486d2924fa57
---

# SMS_ADDomain Class - Configuration Manager | Microsoft Learn

The `SMS_ADDomain` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains Active Directory domains discovered by Configuration Manager Forest Discovery.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADDomain : SMS_BaseClass
{
    UInt32 DomainID;
    String DomainMode;
    String DomainName;
    UInt32 Flags;
    UInt32 ForestID;
    DateTime LastDiscoveryTime;
};
```

## Methods

The `SMS_ADDomain` class does not define any methods.

## Properties

`DomainID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the Active Directory domain.

`DomainMode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The functional level of the Active Directory forest.

| Forest Functional Level |
| --- |
| Windows 2000 |
| Windows Server 2003 interim |
| Windows Server 2003 |
| Windows Server 2008 |
| Windows Server 2008 R2 |

`DomainName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the Active Directory domain.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Flags.

`ForestID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The identifier of Active Directory forest.

`LastDiscoveryTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time this domain was discovered by Active Directory forest discovery.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).