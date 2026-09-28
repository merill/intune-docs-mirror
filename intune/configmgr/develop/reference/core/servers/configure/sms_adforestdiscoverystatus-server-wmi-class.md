---
layout: Conceptual
title: SMS_ADForestDiscoveryStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adforestdiscoverystatus-server-wmi-class
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
description: Learn how to represent the status of Configuration Manager Active Directory Forest Discovery with SMS_ADForestDiscoveryStatus.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f249ebda-030d-f36d-71a4-c174e05c3d60
document_version_independent_id: 0c373779-5a1f-6bba-5d9c-ed0a0cad95ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_adforestdiscoverystatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_adforestdiscoverystatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_adforestdiscoverystatus-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b9573a7-5863-e6b2-bc2b-bbe98da8c928
---

# SMS_ADForestDiscoveryStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ADForestDiscoveryStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the status of Configuration Manager Active Directory Forest Discovery.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADForestDiscoveryStatus : SMS_BaseClass
{
    Boolean DiscoveryEnabled;
    UInt32 DiscoveryStatus;
    UInt32 ForestID;
    DateTime LastDiscoveryTime;
    DateTime LastPublishingTime;
    Boolean PublishingEnabled;
    UInt32 PublishingStatus;
    String SiteCode;
    String SiteName;
};
```

## Methods

The `SMS_ADForestDiscoveryStatus` class does not define any methods.

## Properties

`DiscoveryEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if forest discovery is enabled.

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

`ForestID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the Active Directory forest.

`LastDiscoveryTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time the forest was discovered.

`LastPublishingTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time the forest was published.

`PublishingEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if Active Directory publishing is enabled.

`PublishingStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Publishing status. Possible values are:

| Value | Publishing status |
| --- | --- |
| 0 | UNKNOWN |
| 1 | SUCCEEDED |
| 2 | FAILED |

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The site code where the Active Directory forest was discovered.

`SiteName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The site name where the Active Directory forest was discovered.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).