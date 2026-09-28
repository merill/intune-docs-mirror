---
layout: Conceptual
title: SMS_ADForest Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adforest-server-wmi-class
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
description: An SMS Provider server class that contains Active Directory forests discovered by Configuration Manager Forest Discovery.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0da31854-ae60-0c8c-a200-d9e96c9f51d5
document_version_independent_id: d0644089-f310-a348-4a3f-cff9f7a7a231
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_adforest-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_adforest-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_adforest-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 381ede64-97b1-1fff-26e3-fed0c58174fb
---

# SMS_ADForest Class - Configuration Manager | Microsoft Learn

The `SMS_ADForest` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains Active Directory forests discovered by Configuration Manager Forest Discovery.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADForest : SMS_BaseClass
{
    String Account;
    String CreatedBy;
    DateTime CreatedOn;
    String Description;
    UInt32 DiscoveredADSites;
    UInt32 DiscoveredDomains;
    UInt32 DiscoveredIPSubnets;
    UInt32 DiscoveredTrusts;
    UInt32 DiscoveryStatus;
    Boolean EnableDiscovery;
    String ForestFQDN;
    UInt32 ForestID;
    String ModifiedBy;
    DateTime ModifiedOn;
    String PublishingPath;
    UInt32 PublishingStatus;
};
```

## Methods

The following table lists the methods in the `SMS_ADForest` class.

| Method | Description |
| --- | --- |
| [DeleteDiscoveryData Method in Class SMS_ADForest](deletediscoverydata-method-in-class-sms_adforest) | Removes information gathered by the forest discovery process. |

## Properties

`Account` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Account to discover the Active Directory forest.

`CreatedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User that added the Active Directory forest.

`CreatedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the Active Directory forest was added.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the Active Directory forest.

`DiscoveredADSites` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of discovered Active Directory sites.

`DiscoveredDomains` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of discovered Active Directory domains.

`DiscoveredIPSubnets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of discovered Active Directory IP subnets.

`DiscoveredTrusts` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of discovered Active Directory trusts.

`DiscoveryStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Discovery status. Possible values are:

| Value | Discovery status |
| --- | --- |
| 0 | SUCCEEDED |
| 1 | COMPLETED |
| 2 | ACCESS\_DENIED |
| 3 | FAILED |
| 4 | STOPPED |

`EnableDiscovery` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if Active Directory forest discovery is enabled.

`ForestFQDN` Data type: `String`

Access type: Read/Write

Qualifiers: none

FQDN of the Active Directory forest.

`ForestID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifier of the Active Directory forest.

`ModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User that last modified the Active Directory Forest.

`ModifiedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the Active Directory Forest was last modified.

`PublishingPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

Alternate publishing path.

`PublishingStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Publishing status. Possible values are:

| Value | Publishing status |
| --- | --- |
| 0 | UNKNOWN |
| 1 | SUCCEEDED |
| 2 | FAILED |

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).