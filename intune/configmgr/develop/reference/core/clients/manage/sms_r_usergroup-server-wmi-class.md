---
layout: Conceptual
title: SMS_R_UserGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_usergroup-server-wmi-class
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
description: The SMS_R_UserGroup class is an SMS Provider server class that is generated dynamically at SMS Provider run time and contains discovery data for user group objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ef105670-2f2e-94d2-1aa1-78d391a412a1
document_version_independent_id: d40b6990-8a41-180b-4164-cda7537535ae
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_r_usergroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_r_usergroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_r_usergroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5f6fe473-845f-2627-68e2-8c782e6489b4
---

# SMS_R_UserGroup Class - Configuration Manager | Microsoft Learn

The `SMS_R_UserGroup` Windows Management (WMI) class is an SMS Provider server class, in Configuration Manager, that is generated dynamically at SMS Provider run time and contains discovery data for user group objects.

The following syntax is not defined in Managed Object Format (MOF) code.

## Syntax

```
Class SMS_R_UserGroup : SMS_Resource
{
   String   ActiveDirectoryContainerName[];
   String   ActiveDirectoryOrganizationalUnit[];
   String   ADDomainName;
   String   AgentName[];
   String   AgentSite[];
   DateTime AgentTime[];
   DateTime CreationDate;
   UInt32   GroupType;
   String   Name;
   String   NetworkOperatingSystem;
   UInt8    ObjectGUID[];
   UInt32   ResourceID;
   UInt32   ResourceType;
   String   SID;
   String   UniqueUsergroupName;
   String   UsergroupName;
   String   WindowsNTDomain;
};
```

## Methods

The `SMS_R_UserGroup` class does not define any methods.

## Properties

`ActiveDirectoryContainerName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

Active Directory container name for the group resource.

`ActiveDirectoryOrganizationalUnit` Data type: **String** Array

Access type: Read-only

Qualifiers: None

Active Directory Organizational Unit for the group resource.

`ADDomainName` Data type: **String**

Access type: Read-only

Qualifiers: None

Name of the Active Directory domain for the group resource.

`AgentName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

List of discovery agents that found this resource.

`AgentSite` Data type: **String** Array

Access type: Read-only

Qualifiers: None

List of sites from which the discovery agents ran.

`AgentTime` Data type: **DateTime** Array

Access type: Read-only

Qualifiers: None

List of discovery times.

`Creation Date` Data type: **DateTime** Array

Access type: Read-only

Qualifiers: None

Date and time of creation.

`GroupType` Data type: **UInt32**

Access type: Read-only

Qualifiers: None

Type of group resources on the site.

`Name` Data type: **String**

Access type: Read-only

Qualifiers: None

Group name displayed in the Configuration Manager console.

`NetworkOperatingSystem` Data type: **String**

Access type: Read-only

Qualifiers: None

Free-form string describing the operating system.

`ObjectGUID` Data type: **UInt8** Array

Access type: Read-only

Qualifiers: None

Object GUID of the group resource retrieved from Active Directory.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

See [SMS_Resource Server WMI Class](sms_resource-server-wmi-class).

`ResourceType` Data type: **UInt32**

Access type: Read-only

Qualifiers: None

Type of resources on the site. For more information, see [SMS_ResourceMap Server WMI Class](sms_resourcemap-server-wmi-class).

`SID` Data type: **String**

Access type: Read-only

Qualifiers: None

The Active Directory security ID for the group.

`UniqueUsergroupName` Data type: **String**

Access type: Read-only

Qualifiers: None

Unique user group name in the form domain\group name.

`UsergroupName` Data type: **String**

Access type: Read-only

Qualifiers: None

Unique user group name that represents the resource within the Windows NT domain.

`WindowsNTDomain` Data type: **String**

Access type: Read-only

Qualifiers: None

String representing the Windows NT domain associated with the resource.

## Remarks

You cannot create or update resource instances by using WMI, but must create or update resources using discovery data records. Note, however, that you can delete resource instances by using WMI.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).