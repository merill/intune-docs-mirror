---
layout: Conceptual
title: SMS_PassportForWorkProfileSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_passportforworkprofilesettings-server-wmi-class
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
description: Learn how to represent Windows Hello for Business profile settings in Configuration Manager using SMS_PassportForWorkProfileSettings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 65041688-1928-8de7-550d-e53216445530
document_version_independent_id: 1178eac9-40dd-9860-956f-db3d8e44c2c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_passportforworkprofilesettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_passportforworkprofilesettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_passportforworkprofilesettings-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/798bd9d1-9cc5-4fc7-b0e5-8699d1f6ce2a
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b5dc5f65-34a8-4bfc-9917-97d1e20c88b2
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5c026063-6f15-e683-5493-787645f0d719
---

# SMS_PassportForWorkProfileSettings Class - Configuration Manager | Microsoft Learn

The `SMS_PassportForWorkProfileSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Windows Hello for Business profile settings.

Note

Windows Hello for Business was previously known as Microsoft Passport for Work.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PassportForWorkProfileSettings : SMS_SettingsDefinitionBase
{
    String ApplicabilityCondition;
    String CategoryInstance_UniqueIDs[];
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 CIType_ID;
    UInt32 CIVersion;
    UInt64 ConfigurationFlags;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateLastModified;
    DateTime EffectiveDate;
    UInt32 EULAAccepted;
    Boolean EULAExists;
    DateTime EULASignoffDate;
    String EULASignoffUser;
    UInt32 ExecutionContext;
    Boolean IsBroken;
    Boolean IsBundle;
    Boolean IsDigest;
    Boolean IsEnabled;
    Boolean IsExpired;
    Boolean IsHidden;
    Boolean IsLatest;
    Boolean IsQuarantined;
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

The `SMS_PassportForWorkProfileSettings` class does not define any methods.

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: None

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers:[unique, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [bits("COMPLIANCE\_POLICY(0)"), read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"),read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`InUse` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: [unique,not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`PermittedUses` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [bitmap, bitvalues, read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData Array`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

See [SMS_SettingsDefinitionBase Server WMI Class](sms_settingsdefinitionbase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).