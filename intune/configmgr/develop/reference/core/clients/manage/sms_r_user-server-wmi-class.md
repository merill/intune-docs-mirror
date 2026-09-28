---
layout: Conceptual
title: SMS_R_User Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_user-server-wmi-class
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
description: In Configuration Manager, the SMS_R_User WMI class is an SMS Provider server class that is generated dynamically at SMS Provider run time and contains data discovery for users within a Configuration Manager site hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 389cf858-dc6b-ddf1-bf66-10052ddd224e
document_version_independent_id: 2c573ec4-b082-e157-c98a-4f90365b0753
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_r_user-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_r_user-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_r_user-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: adf93f4f-a0ad-24f0-c831-edda0449ef85
---

# SMS_R_User Class - Configuration Manager | Microsoft Learn

The `SMS_R_User` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is generated dynamically at SMS Provider run time and contains data discovery for users within a Configuration Manager site hierarchy.

The following syntax is not defined in Managed Object Format (MOF) code.

## Syntax

```
Class SMS_R_User : SMS_Resource
{
   String   AgentName[];
   String   AgentSite[];
   DateTime  AgentTime[];
   DateTime  CreationDate;
   String   DistinguishedName;
   String   FullUserName;
   String   Mail;
   String   Name;
   String   NetworkOperatingSystem;
   UInt8   ObjectGUID;
   UInt32   PrimaryGroupID;
   UInt32   ResourceID;
   UInt32   ResourceType;
   String   SID;
   String   UniqueUserName;
   UInt32   UserAccountControl;
   String   UserContainerName[];
   String   UserGroupName[];
   String   UserName;
   String   UserOUName[];
   String   WindowsNTDomain;
};
```

## Methods

The `SMS_R_User` class does not define any methods.

## Properties

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

`CreationDate` Data type: **DateTime**

Access type: Read-only

Qualifiers: None

The date the record was first created, which is the date when the resource was discovered.

`DistinguishedName` Data type: **String**

Access type: Read-only

Qualifiers: None

Distinguished name of the user resource retrieved from Active Directory.

`FullUserName` Data type: **String**

Access type: Read-only

Qualifiers: None

For Windows NT users, the value of the **Full Name** property of User Properties; for Windows 2000 users, the value of the **Display Name** property in Active Directory.

`Mail` Data type: **String**

Access type: Read-only

Qualifiers: None

Mail address of the user resource retrieved from Active Directory.

`Name` Data type: **String**

Access type: Read-only

Qualifiers: None

User name displayed in the Configuration Manager console. Its format is UniqueUserName (FullUserName), where FullUserName is included only if it contains a value.

`NetworkOperatingSystem` Data type: **String**

Access type: Read-only

Qualifiers: None

Free-form string describing the operating system.

`ObjectGUID` Data type: **UInt8**

Access type: Read-only

Qualifiers: None

Object GUID of the user resource retrieved from Active Directory.

`PrimaryGroupID` Data type: **UInt32**

Access type: Read-only

Qualifiers: None

Primary group ID of the user resource retrieved from Active Directory.

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

Security identifier of the user resource retrieved from Active Directory.

`UniqueUserName` Data type: **String**

Access type: Read-only

Qualifiers: None

Unique user name in the form domain\user name.

`UserAccountControl` Data type: **UInt32**

Access type: Read-only

Qualifiers: None

User account control value retrieved from Active Directory.

`UserContainerName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

An array of Active Directory container names to which the user belongs.

`UserGroupName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

An array of Active Directory group names to which the user belongs.

`UserName` Data type: **String**

Access type: Read-only

Qualifiers: None

User logon name.

`UserOUName` Data type: **String** Array

Access type: Read-only

Qualifiers: None

An array of Active Directory organizational units (OUs) to which the user belongs.

`WindowsNTDomain` Data type: **String**

Access type: Read-only

Qualifiers: None

Windows NT domain that is associated with the resource.

## Remarks

You cannot create or update resource instances by using WMI, but must create or update resources by using data discovery records. Note, however, that you can delete resource instances by using WMI.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).