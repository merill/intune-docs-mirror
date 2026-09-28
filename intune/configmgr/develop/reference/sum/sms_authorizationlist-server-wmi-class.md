---
layout: Conceptual
title: SMS_AuthorizationList Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class
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
description: A collection of SMS_SoftwareUpdate objects for the software updates available on the site and authorized for deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a8fc24d3-14f2-1243-896b-0c9de8b2e8aa
document_version_independent_id: 0584f696-8d90-7ce0-f750-64e9542915bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e6ea263b-a9c3-761b-d5fc-2090619bea4a
---

# SMS_AuthorizationList Class - Configuration Manager | Microsoft Learn

The `SMS_AuthorizationList` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a collection of `SMS_SoftwareUpdate` objects for the software updates available on the site and authorized for deployment. Use of an authorization list is optional in a software update deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AuthorizationList : SMS_ConfigurationItemBaseClass
{
    String ApplicabilityCondition;
    UInt32 AssociatedAutoRuleID;
    String CategoryInstance_UniqueIDs[];
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 CIType_ID;
    UInt32 CIVersion;
    UInt64 ConfigurationFlags;
    Boolean ContainsExpiredUpdates;
    Boolean ContainsSupersededUpdates;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateLastModified;
    DateTime EffectiveDate;
    UInt32 EULAAccepted;
    Boolean EULAExists;
    DateTime EULASignoffDate;
    String EULASignoffUser;
    UInt32 ExecutionContext;
    Boolean IsBundle;
    Boolean IsDeployed;
    Boolean IsDigest;
    Boolean IsEnabled;
    Boolean IsExpired;
    Boolean IsHidden;
    Boolean IsLatest;
    Boolean IsProvisioned;
    Boolean IsQuarantined;
    Boolean IsSuperseded;
    Boolean IsUserDefined;
    String LastModifiedBy;
    DateTime LastStatusTime;
    String LocalizedCategoryInstanceNames[];
    String LocalizedDescription;
    String LocalizedDisplayName;
    SMS_CI_LocalizedProperties LocalizedInformation[];
    String LocalizedInformativeURL;
    UInt32 LocalizedPropertyLocaleID;
    UInt32 ModelID;
    String ModelName;
    UInt32 NumberOfCollectionsDeployed;
    UInt32 NumberOfExpiredUpdates;
    UInt32 NumberOfUpdates;
    UInt32 NumCompliant;
    UInt32 NumNonCompliant;
    UInt32 NumTotal;
    UInt32 NumUnknown;
    UInt32 PercentCompliant;
    UInt32 PermittedUses;
    String PlatformCategoryInstance_UniqueIDs[];
    UInt32 PlatformType;
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
    UInt32 SDMPackageVersion;
    String SDMPackageXML;
    String SecuredScopeNames[];
    String SedoObjectVersion;
    String SourceSite;
    UInt32 Updates[];
};
```

## Methods

The following table lists the methods in the `SMS_AuthorizationList` class.

| Method | Description |
| --- | --- |
| [RunAuthListStatusSummarization Method in Class SMS_AuthorizationList](runauthliststatussummarization-method-in-class-sms_authorizationlist) | Updates summarized results for a particular update group. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`AssociatedAutoRuleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Associated auto deployment rule ID.

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers:[unique, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

For this class, the type ID is SoftwareUpdateAuthorizationList (9).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the Authorization List contains one or more expired updates.

`ContainsSupersededUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the Authorization List contains one or more superseded updates.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

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

Execution context that the configuration item should be evaluated under.

| Value | Configuration item |
| --- | --- |
| 0 | System |
| 1 | User |

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsDeployed` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

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

`IsProvisioned` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the content is downloaded for all updates in the Authorization List.

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastStatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last status update time.

`LocalizedCategoryInstanceNames` Data type: `String` Array

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

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read/Write

Qualifiers: [lazy]

Language-specific localized information about the authorization list:

- String DisplayName
- String Description
- String InformativeURL
- UInt32 LocaleID

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

    Qualifiers: [unique, not\_null]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

    `NumberOfCollectionsDeployed` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of collections that the Authorization List has been deployed to.

    `NumberOfExpiredUpdates` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of expired updates in the update group.

    `NumberOfUpdates` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of updates in the update group.

    `NumCompliant` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of client machines where this Authorization List is compliant.

    `NumNonCompliant` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of client machines where this Authorization List is non-compliant.

    `NumTotal` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Total count of client machines for this Authorization List.

    `NumUnknown` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Count of client machines where this Authorization List is in an unknown state.

    `PercentCompliant` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    Percentage of client machines that are compliant for this configuration item.

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

    `SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

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

    Qualifiers: [SizeLimit("3")]

    See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

    `Updates` Data type: `UInt32` Array

    Access type: Read/Write

    Qualifiers: [lazy]

    Collection of IDs of `SMS_SoftwareUpdate` objects. Each ID is represented by the `CI_ID` property of the corresponding update object.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Use of this class is optional. An `SMS_AuthorizationList` object is created based on criteria that are chosen by the administrator for deployment of selected `SMS_SoftwareUpdate` objects. The authorization list is used by an [SMS_UpdatesAssignment Server WMI Class](sms_updatesassignment-server-wmi-class) object to create a deployment.

    An `SMS_AuthorizationList` object is a type of configuration item, as is each software update. Therefore, the authorization list is an example of a configuration item that bundles other configuration items. Both `SMS_AuthorizationList` and `SMS_SoftwareUpdate` are derived from SMS\_ConfigurationItemBaseClass Server WMI Class, which defines an `IsBundle` property. When building an authorization list, this property of each update is set to `true` to indicate that the update is part of a bundle.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).