---
layout: Conceptual
title: SMS_GlobalCondition Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_globalcondition-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that is used to create, retrieve, modify, or delete global conditions of type Setting or Expression.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5c81162b-a440-2e7b-e2cd-060467b2706a
document_version_independent_id: dd51c746-25d1-d041-4478-d10dcd10b29a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_globalcondition-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_globalcondition-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_globalcondition-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 587259c3-d87f-a5f9-6e60-66d0205cdb89
---

# SMS_GlobalCondition Class - Configuration Manager | Microsoft Learn

The `SMS_GlobalCondition` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to create, retrieve, modify, or delete global conditions of type Setting or Expression.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_GlobalCondition : SMS_ConfigurationItemBaseClass
{
    String ApplicabilityCondition;
    String CategoryInstance_UniqueIDs[];
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 CIType_ID;
    UInt32 CIVersion;
    UInt64 ConfigurationFlags;
    String CreatedBy;
    String DataType;
    DateTime DateCreated;
    DateTime DateLastModified;
    DateTime EffectiveDate;
    UInt32 EULAAccepted;
    Boolean EULAExists;
    DateTime EULASignoffDate;
    String EULASignoffUser;
    UInt32 ExecutionContext;
    UInt32 GlobalConditionType;
    Boolean InUse;
    Boolean IsBundle;
    Boolean IsDigest;
    Boolean IsEnabled;
    Boolean IsExpired;
    Boolean IsHidden;
    Boolean IsLatest;
    Boolean IsQuarantined;
    Boolean IsReadOnly;
    Boolean IsSuperseded;
    Boolean IsUserDefined;
    String LastModifiedBy;
    String LocalizedCategoryInstanceNames[];
    String LocalizedDescription;
    String LocalizedDisplayName;
    SMS_CI_LocalizedEulas LocalizedEulas[];
    SMS_CI_LocalizedProperties LocalizedInformation[];
    String LocalizedInformativeURL;
    UInt32 LocalizedPropertyLocaleID;
    UInt32 ModelID;
    String ModelName;
    UInt32 PermittedUses;
    String PlatformCategoryInstance_UniqueIDs[];
    UInt32 PlatformType;
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
    UInt32 SDMPackageVersion;
    String SDMPackageXML;
    String SecuredScopeNames[];
    String SedoObjectVersion;
    String SourceSite;
};
```

## Methods

The `SMS_GlobalCondition` class does not define any methods.

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, sizelimit("512"]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, key]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, unique]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DataType` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Returned data type of the global condition.

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`GlobalConditionType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

Type of the global condition.

| Value | Global condition type |
| --- | --- |
| 1 | Setting |
| 2 | Expression |

`InUse` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the global condition is referenced by an application; otherwise, `false`.

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsReadOnly` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the global condition is a default global condition; otherwise, `false`.

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas` Array

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`PermittedUses` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [bitmap, bitvalues, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData Array`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).