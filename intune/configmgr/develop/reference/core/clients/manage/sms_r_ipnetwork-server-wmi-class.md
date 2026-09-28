---
layout: Conceptual
title: SMS_R_IPNetwork Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_ipnetwork-server-wmi-class
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
description: The SMS_R_IPNetwork WMI class is an SMS Provider server class, in Configuration Manager, that is generated dynamically and contains data for resources discovered by the Network Discovery Agent.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1c460e1f-4eb1-3334-8592-27227705071a
document_version_independent_id: d00ee4d7-b0fb-662a-b3e6-289e38ceff08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_r_ipnetwork-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_r_ipnetwork-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_r_ipnetwork-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e8bd6818-c178-fdfc-ecb2-259509fd4494
---

# SMS_R_IPNetwork Class - Configuration Manager | Microsoft Learn

The `SMS_R_IPNetwork` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is generated dynamically at SMS Provider run time and contains discovery data for resources discovered by the Network Discovery Agent.

The following syntax is not defined in the Managed Object Format (MOF) code.

## Syntax

```
Class SMS_R_IPNetwork : SMS_Resource
{
     String AgentName[];
     String AgentSite[];
     DateTime AgentTime[];
     DateTime CreationDate;
     String Name;
     UInt32 ResourceID;
     UInt32 ResourceType;
     String SubnetAddress;
     String SubnetMask;
     String SubnetName;
     String SubnetTopology;
};
```

## Methods

The `SMS_R_IPNetwork` class does not define any methods.

## Properties

`AgentName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

Names of agents that discovered the resource.

`AgentSite` Data type: **String** Array

Access type: Read-only

Qualifiers: None

List of sites from which the agent ran.

`AgentTime` Data type: **DateTime** Array

Access type: Read-only

Qualifiers: None

List of discovery times.

`CreationDate` Data type: **DateTime**

Access type: Read-only

Qualifiers: None

Creation time stamp of the discovered resource.

`Name` Data type: **String**

Access type: Read-only

Qualifiers: None

Name of the resource. This value might be blank.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

See [SMS_Resource Server WMI Class](sms_resource-server-wmi-class).

`ResourceType` Data type: **UInt32**

Access type: Read-only

Qualifiers: None

Type of resources on the site. Because other types of resources might be added before network discovery is enabled, this property might be set to any value equal to or greater than 6.

`SubnetAddress` Data type: **String**

Access type: Read-only

Qualifiers: None

IP network address. This value can contain wildcards.

`SubnetMask` Data type: **String**

Access type: Read-only

Qualifiers: None

Subnet mask for the subnet number.

`SubnetName` Data type: **String**

Access type: Read-only

Qualifiers: None

Name of the subnet.

`SubnetTopology` Data type: **String**

Access type: Read-only

Qualifiers: None

Topology of the subnet.

## Remarks

This class is not available on sites where the agent is not enabled. The Network Discovery Agent is not enabled at the time Configuration Manager is installed. You must enable the agent by using the Configuration Manager console or by updating the site control file.

Although you can specify an IP network resource type for a collection, you cannot distribute software to its resources.

You cannot create or update an instance of this class, but you can delete an instance.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).