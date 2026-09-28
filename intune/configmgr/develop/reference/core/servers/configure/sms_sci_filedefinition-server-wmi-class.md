---
layout: Conceptual
title: SMS_SCI_FileDefinition Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_filedefinition-server-wmi-class
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
description: Learn how to represent the basic properties of the site control file in Configuration Manager using SMS_SCI_FileDefinition.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d584ff0a-372c-b72e-a3e4-25c75a25bf2e
document_version_independent_id: 1e60a457-eb8a-8c88-ab75-15033ac7b14b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_filedefinition-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_filedefinition-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_filedefinition-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 7e5a49f8-6d6c-9ef9-f297-4b670e5df611
---

# SMS_SCI_FileDefinition Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_FileDefinition` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the basic properties of the site control file.

Note

This class is vital to the operation of the site control infrastructure. Changing the values for an existing site might render the site control file unusable for further configuration. Existing objects for functioning sites should not be changed.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_FileDefinition : SMS_SiteControlItem
{
     String Comment;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     String OriginatingSite;
     UInt32 SerialNumber;
     String SiteCode;
     String TargetSite;
};
```

## Methods

The `SMS_SCI_FileDefinition` class doesn't define any methods.

## Properties

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Free-format comment. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`OriginatingSite` Data type: `String`

Access type: Read-only

Qualifiers: None

Site that originated the creation of the value indicated by `TargetSite`. The default value is "".

`SerialNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Serial number of the actual site control file. It's incremented each time the site control file changes.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`TargetSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

Site for which you're creating the site control file. The default value is "".

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).