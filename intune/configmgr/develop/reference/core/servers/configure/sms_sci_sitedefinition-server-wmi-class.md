---
layout: Conceptual
title: SMS_SCI_SiteDefinition Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sitedefinition-server-wmi-class
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
description: Learn how to use the SMS_SCI_SiteDefinition class which contains general definitions for the site and accounts used by Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8f24878d-2e6b-c688-4f64-120362b1f3ed
document_version_independent_id: 6eff4b71-6d51-4cf6-4651-4f990ae0a0a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sitedefinition-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_sitedefinition-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_sitedefinition-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 5b9be262-769b-2007-c169-3400d09b771d
---

# SMS_SCI_SiteDefinition Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_SiteDefinition` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains general definitions for the site (for example, name) and for accounts (for example, SQL) used by Configuration Manager server components.

Note

This class is vital to the operation of the site control infrastructure. Changing the values for an existing site might render the site control file unusable for further configuration. Existing objects for functioning sites should not be changed.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_SiteDefinition : SMS_SiteControlItem
{
     String AddressPublicKey;
     UInt32 FileType;
     String InstallDirectory;
     String ItemName;
     String ItemType;
     String ParentSiteCode;
     SMS_EmbeddedPropertyList PropLists[];
     SMS_EmbeddedProperty Props[];
     String ServiceAccount;
     String ServiceAccountDomain;
     String ServiceAccountPassword;
     String ServiceExchangeKey;
     String ServicePlaintextAccount;
     String ServicePublicKey;
     String SiteCode;
     String SiteName;
     String SiteServerDomain;
     String SiteServerName;
   String SiteServerPlatform;
     UInt32 SiteType;
     String SQLAccount;
     String SQLAccountPassword;
     String SQLDatabaseName;
     String SQLPublicKey;
     String SQLServerName;
};
```

## Methods

The `SMS_SCI_SiteDefinition` class does not define any methods.

## Properties

`AddressPublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`InstallDirectory` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory on the site server where the Configuration Manager tree starts. The default value is "".

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ParentSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

Three-letter site code of the parent site (if there is one). The default value is "".

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the site.

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the site.

`ServiceAccount` Data type: String

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`ServiceAccountDomain` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`ServiceAccountPassword` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`ServiceExchangeKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

Public exchange key used to encrypt the value of `ServicePublicKey`. Provide no value for this property if `ServicePublicKey` is not encrypted.

`ServicePlaintextAccount` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`ServicePublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`SiteName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Unique friendly site name of the site server. The default value is "".

`SiteServerDomain` Data type: `String`

Access type: Read/Write

Qualifiers: None

Domain in which the site server participates. The default value is "".

`SiteServerName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the Windows NT site server. The default value is "".

`SiteServerPlatform` Data type: `String`

Access type: Read/Write

Qualifiers: [StringEnumeration]

Processor platform of the site server. Possible values are:

- AMD64

    `SiteType` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [ResIDValueLookup("SiteType")]

    Type of site. Possible values are listed for the `Type` property of [SMS_Site Server WMI Class](sms_site-server-wmi-class).

    For this class, the default value is PRIMARY (2).

| Value | Site type |
| --- | --- |
| 1 | Secondary |
| 2 | Primary |
| 4 | CAS |

`SQLAccount` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`SQLAccountPassword` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`SQLDatabaseName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the SQL Server database on the server. The default value is "".

`SQLPublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

This property is deprecated.

`SQLServerName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the computer running SQL Server for this installation. The default value is "".

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).