---
layout: Conceptual
title: SMS_ADSite Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adsite-server-wmi-class
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
description: Learn how the SMS_ADSite class is an SMS Provider server class that contains Active Directory sites discovered by Configuration Manager Forest Discovery.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 77ac27ec-966b-6a80-6be7-1eb9c33d7846
document_version_independent_id: 394cd4f2-feda-f794-f914-f1316f8b71e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_adsite-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_adsite-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_adsite-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e1d69365-278d-1146-2f3a-af1518c269f0
---

# SMS_ADSite Class - Configuration Manager | Microsoft Learn

The `SMS_ADSite` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains Active Directory sites discovered by Configuration Manager Forest Discovery.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADSite : SMS_BaseClass
{
    String ADSiteDescription;
    String ADSiteLocation;
    String ADSiteName;
    UInt32 Flags;
    UInt32 ForestID;
    DateTime LastDiscoveryTime;
    UInt32 SiteID;
};
```

## Methods

The `SMS_ADSite` class does not define any methods.

## Properties

`ADSiteDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the Active Directory site.

`ADSiteLocation` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Location of the Active Directory site.

`ADSiteName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the Active Directory site.

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

The last time this Active Directory site was discovered by Active Directory forest discovery.

`SiteID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The ID of the site.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).