---
layout: Conceptual
title: SMS_ADSubnet Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adsubnet-server-wmi-class
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
description: Learn how to use SMS_ADSubnet class as an SMS Provider server class that contains Active Directory subnets discovered by CM Forest Discovery.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3d80664d-c370-10fb-03d0-04278819654f
document_version_independent_id: d25995b2-1b48-670d-fec9-ad50918ea295
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_adsubnet-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_adsubnet-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_adsubnet-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 8efc8e26-8b18-b2cb-17a6-658d342b2163
---

# SMS_ADSubnet Class - Configuration Manager | Microsoft Learn

The `SMS_ADSubnet` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains Active Directory subnets discovered by Configuration Manager Forest Discovery.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADSubnet : SMS_BaseClass
{
    String ADSubnetDescription;
    String ADSubnetLocation;
    String ADSubnetName;
    UInt32 Flags;
    UInt32 ForestID;
    DateTime LastDiscoveryTime;
    UInt32 SiteID;
    UInt32 SubnetID;
};
```

## Methods

The `SMS_ADSubnet` class does not define any methods.

## Properties

`ADSubnetDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the Active Directory subnet.

`ADSubnetLocation` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Location of the Active Directory subnet.

`ADSubnetName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the Active Directory subnet.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Flags.

`ForestID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the Active Directory forest.

`LastDiscoveryTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time this Active Directory subnet was discovered by Active Directory discovery.

`SiteID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Reference to the `SMS_ADSite SiteID` value.

`SubnetID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The subnet ID.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).