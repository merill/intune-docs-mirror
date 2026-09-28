---
layout: Conceptual
title: SMS_ConfigurationBaselineInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class
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
description: An SMS Provider server class that represents a baseline configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a3df30b3-6415-e49e-7111-e27ee1bf3cc8
document_version_independent_id: c82d99b9-7656-c0d5-aced-6aeed9d2a9f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5a9af532-2d12-1b27-4a63-8fdbcf3b6cc4
---

# SMS_ConfigurationBaselineInfo Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigurationBaselineInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a baseline configuration item. For more information about this type of configuration item, see [SMS_BaselineAssignment Server WMI Class](sms_baselineassignment-server-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationBaselineInfo : SMS_ConfigurationItemBaseClass
{
      UInt32 ActivatedCount;
      String ApplicabilityCondition;
      UInt32 AssignedCount;
      String CategoryInstance_UniqueIDs[];
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIType_ID;
      UInt32 CIVersion;
      UInt32 ComplianceCount;
      Real64 CompliantPercentage;
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
      UInt32 FailureCount;
      Boolean InUse;
      Boolean IsAssigned;
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
      String LocalizedInformativeURL;
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ModelID;
      String ModelName;
      UInt32 NonComplianceCount;
      UInt32 PermittedUses;
      String PlatformCategoryInstance_UniqueIDs[];
      UInt32 PlatformType;
      SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
      UInt32 SDMPackageVersion;
      String SDMPackageXML;
      String SecuredScopeNames[];
      String SedoObjectVersion;
      UInt32 Severity;
      String SourceSite;
      Real64 TargetCompliance;
};
```

## Methods

The `SMS_ConfigurationBaselineInfo` class does not define any methods.

## Properties

`ActivatedCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that have evaluated the configuration item.

`ApplicabilityCondition` Data type: `String`

Access type: Read

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`AssignedCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that are targeted with the configuration item.

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read

Qualifiers: None

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read

Qualifiers:[unique, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class)..

For this class, the type ID is Baseline (2).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ComplianceCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of computers that are compliant with the configuration item.

`CompliantPercentage` Data type: `Real64`

Access type: Read/Write

Qualifiers: none

The property is deprecated. Use the information contained in the [SMS_DeploymentSummary Server WMI Class](../apps/sms_deploymentsummary-server-wmi-class) instead.

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`FailureCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of computers that failed to evaluate the configuration item.

`InUse` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the configuration item is in use. A configuration item is used, if it is referenced by other baseline or its setting is referenced by other configuration item.

`IsAssigned` Data type: `Boolean`

Access type: Read

Qualifiers: None

`true` if the configuration item is assigned. The default value is `false`.

`IsBundle` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the configuration item is broken, otherwise, the value is `false`.

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

This property is not used for desired configuration management.

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read

Qualifiers: [unique, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`NonComplianceCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of computers that are not compliant with the configuration item.

`PermittedUses` Data type: `UInt32`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [bitmap, bitvalues, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

Access type: Read

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read

Qualifiers: [lazy]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`Severity` Data type: `UInt32`

Access type: Read

Qualifiers: None

The noncompliance severity of the configuration item.

`SourceSite` Data type: `String`

Access type: Read

Qualifiers: [SizeLimit("3")]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](sms_configurationitemlatestbaseclass-server-wmi-class).

`TargetCompliance` Data type: `Real64`

Access type: Read/Write

Qualifiers: none

The property is deprecated. Use the information contained in the [SMS_DeploymentSummary Server WMI Class](../apps/sms_deploymentsummary-server-wmi-class) class instead.

## Remarks

Class qualifiers for this class include:

- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application can use this class to create a baseline. After creating the object, the application should set the `CIType_ID` property to Baseline (2). When the object is properly configured, the application can use the [SMS_BaselineAssignment Server WMI Class](sms_baselineassignment-server-wmi-class) class to populate it with other configuration items and corresponding rules.

    For information on the use of this class, see How to List Configuration Assignments and How to Assign Configuration Baselines. An example for baseline configuration is provided in Configuration Baseline Example 1.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).