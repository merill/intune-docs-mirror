---
layout: Conceptual
title: SMS_SoftwareUpdate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class
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
description: The SMS_SoftwareUpdate WMI class exposes software update information available on a site and serves as the core class for software updates.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: defc404c-c638-ddd2-1d39-ae67020c42e8
document_version_independent_id: d097d528-7f33-86ce-30b8-1666b10e0944
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2f25910d-e28f-871c-9b03-64bda76d7562
---

# SMS_SoftwareUpdate Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareUpdate` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that exposes software update information available on a site and serves as the core class for software updates.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareUpdate : SMS_ConfigurationItemBaseClass   
{   
      String ApplicabilityCondition;   
      String ArticleID;   
      String BulletinID;   
      String CategoryInstance_UniqueIDs[];   
      UInt32 CI_ID;   
      String CI_UniqueID;   
      UInt32 CIType_ID;   
      UInt32 CIVersion;   
      UInt64 ConfigurationFlags;  
      String CreatedBy;   
      UInt32 CustomSeverity;   
      String CustomSeverityName;   
      DateTime DateCreated;   
      DateTime DateLastModified;   
      DateTime DatePosted;   
      DateTime DateRevised;   
      DateTime EffectiveDate;   
      UInt32 EULAAccepted;   
      Boolean EULAExists;   
      DateTime EULASignoffDate;   
      String EULASignoffUser;   
      UInt32 ExecutionContext;   
      Boolean IsBundle;   
      Boolean IsContentProvisioned;   
      Boolean IsDeployable;   
      Boolean IsDeployed;   
      Boolean IsDigest;   
      Boolean IsEnabled;   
      Boolean IsExpired;   
      Boolean IsHidden;   
      Boolean IsLatest;  
      Boolean IsMetadataOnlyUpdate;   
      Boolean IsOfflineServiceable;   
      Boolean IsQuarantined;   
      Boolean IsSuperseded;   
      Boolean IsUserDefined;   
      String LastModifiedBy;   
      DateTime LastStatusTime;   
      String LocalizedCategoryInstanceNames[];   
      String LocalizedDescription;   
      String LocalizedDisplayName;   
      SMS_CI_LocalizedEulas LocalizedEulas[];   
      SMS_CI_LocalizedProperties LocalizedInformation[];   
      String LocalizedInformativeURL;   
      UInt32 LocalizedPropertyLocaleID;   
      UInt32 MaxExecutionTime;   
      UInt32 ModelID;  
      String ModelName;   
      UInt32 NumMissing;   
      UInt32 NumNotApplicable;   
      UInt32 NumPresent;   
      UInt32 NumTotal;   
      UInt32 NumUnknown;   
      UInt32 PercentCompliant;   
      UInt32 PermittedUses;   
      String PlatformCategoryInstance_UniqueIDs[];   
      UInt32 PlatformType;   
      Boolean RequiresExclusiveHandling;   
      UInt32 RevisionNumber;   
      SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];   
      UInt32 SDMPackageVersion;   
      String SDMPackageXML;   
      String SecuredScopeNames[];   
      String SedoObjectVersion;   
      UInt32 Severity;   
      String SeverityName;   
      SInt64 Size;   
      String SourceSite;   
      String UpdateLocales[];   
};  
```

## Methods

The following table shows the methods in `SMS_SoftwareUpdate`.

| Method | Description |
| --- | --- |
| [AcceptEULA Method in Class SMS_SoftwareUpdate](accepteula-method-in-class-sms_softwareupdate) | Accepts or declines the Microsoft Software License Terms of a software update. |
| FilterUpdates Method in Class SMS\_SoftwareUpdate | For internal use only. |
| [GetEULA Method in Class SMS_SoftwareUpdate](geteula-method-in-class-sms_softwareupdate) | Gets the localized Microsoft Software License Terms content of a software update. |
| [SetEnforcement Method in Class SMS_SoftwareUpdate](setenforcement-method-in-class-sms_softwareupdate) | Sets policy enforcement of a software update. |
| [SyncNow Method in Class SMS_SoftwareUpdate](syncnow-method-in-class-sms_softwareupdate) | Performs a manual synchronization of the Software Update Point. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("512"), not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`ArticleID` Data type: `String`

Access type: Read-only

Qualifiers: [read, SizeLimit("64"), not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`BulletinID` Data type: `String`

Access type: Read-only

Qualifiers: [read, SizeLimit("64"), not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers:[unique, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

For this class, the type ID is SoftwareUpdate (1) or SoftwareUpdateBundle (8).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: [bits("COMPLIANCE\_POLICY(0)"), read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CustomSeverity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`CustomSeverityName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`DatePosted` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`DateRevised` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsContentProvisioned` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsDeployable` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsDeployed` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsMetadataOnlyUpdate` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsOfflineServiceable` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [SizeLimit("512"), read, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LastStatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: read

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read-only

Qualifiers: [read, lazy]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`MaxExecutionTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`NumMissing` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`NumNotApplicable` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`NumPresent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`NumTotal` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`NumUnknown` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`PercentCompliant` Data type: `UInt32`

Access type: Read

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`PermittedUses` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String` array

Access type: Read/Write

Qualifiers: none

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`RequiresExclusiveHandling` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`RevisionNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SecuredScopeNames` Data type: `String` Array

Access type: Read-only

Qualifiers: none

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: none

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`Severity` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SeverityName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`Size` Data type: `SInt64`

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

`UpdateLocales` Data type: `String` Array

Access type: Read-only

Qualifiers: [read]

See [SMS_SoftwareUpdateBase Server WMI Class](sms_softwareupdatebase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see Configuration Manager Class and Property Qualifiers.

    An `SMS_SoftwareUpdate` object is a type of configuration item, defined by SMS\_ConfigurationItemBaseClass Server WMI Class. Use `SMS_SoftwareUpdate` to determine the compliance of software updates using the Software Updates feature in Configuration Manager.

    Software update content must be downloaded manually. To identify which contents need to be downloaded, your application queries [SMS_CIToContent Server WMI Class](sms_citocontent-server-wmi-class) and obtains the list of `ContentID` properties matching the specific language criteria. With this list, the application can obtain the associated download URL and the related properties for the content files from [SMS_CIContentFiles Server WMI Class](sms_cicontentfiles-server-wmi-class).

    When the update content has been determined, the application optionally prepares the update for deployment using an [SMS_AuthorizationList Server WMI Class](sms_authorizationlist-server-wmi-class) object to create an authorized list of updates. Your application also has the option of implementing [SMS_Template Server WMI Class](sms_template-server-wmi-class) to create a custom deployment template.

Note

When it is building an authorization list to include the software update, the application must set the `IsBundle` property of `SMS_SoftwareUpdate` to `true` to indicate that the update is part of a bundle. For more information, see [SMS_AuthorizationList Server WMI Class](sms_authorizationlist-server-wmi-class).

When the application is ready to deploy the software update, it uses an [SMS_UpdatesAssignment Server WMI Class](sms_updatesassignment-server-wmi-class) object to create a deployment.

You cannot import, create, or configure software updates in the Desired Configuration Management node. These functions are made available to configuration baselines through the Software Updates feature when software updates are downloaded. Therefore, software update configuration items can be selected to be included in configuration baselines even though they are not displayed under the Configuration Items node.

See How to Enumerate Updates Matching a Specific Criteria for a discussion of queries that you can use to enumerate the information about multiple software updates.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).