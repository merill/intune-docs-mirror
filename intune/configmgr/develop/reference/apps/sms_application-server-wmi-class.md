---
layout: Conceptual
title: SMS_Application Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class
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
description: The SMS_Application Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 806132ac-a0d4-3659-f682-94ba3121044b
document_version_independent_id: 1992cf32-f8cd-47f9-8722-072ade3e3b6f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_application-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_application-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 28eb2d30-0daf-ea15-839f-5b4c4edbff68
---

# SMS_Application Class - Configuration Manager | Microsoft Learn

The `SMS_Application` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Application : SMS_ConfigurationItemBaseClass
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
    UInt32 Featured;
    Boolean HasContent;
    Boolean IsBundle;
    Boolean IsDeployable;
    Boolean IsDeployed;
    Boolean IsDigest;
    Boolean IsEnabled;
    Boolean IsExpired;
    Boolean IsHidden;
    Boolean IsLatest;
    Boolean IsQuarantined;
    Boolean IsSuperseded;
    Boolean IsSuperseding;
    Boolean IsUserDefined;
    String LastModifiedBy;
    String LocalizedCategoryInstanceNames[];
    String LocalizedDescription;
    String LocalizedDisplayName;
    String LocalizedInformativeURL;
    UInt32 LocalizedPropertyLocaleID;
    UInt32 LogonRequirement;
    String Manufacturer;
    String ModelName;
    UInt32 ModelID;
    UInt32 NumberOfDependentDTs;
    UInt32 NumberOfDependentTS;
    UInt32 NumberOfDeployments;
    UInt32 NumberOfDeploymentTypes;
    UInt32 NumberOfDevicesWithApp;
    UInt32 NumberOfDevicesWithFailure;
    UInt32 NumberOfSettings;
    UInt32 NumberOfUsersWithApp;
    UInt32 NumberOfUsersWithFailure;
    UInt32 NumberOfUsersWithRequest;
    UInt32 NumberOfVirtualEnvironments;
    String PackageID;
    UInt32 PermittedUses;
    String PlatformCategoryInstance_UniqueIDs[];
    UInt32 PlatformType;
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
    UInt32 SDMPackageVersion;
    String SDMPackageXML;
    String SecuredScopeNames[];
    String SedoObjectVersion;
    String SoftwareVersion;
    UInt32 SourceCIVersion;
    String SourceModelName;
    String SourceSite;
    DateTime SummarizationTime;
};
```

## Methods

The following table lists the methods in the `SMS_Application` class.

| Method | Description |
| --- | --- |
| [GetCIDocumentBody Method in Class SMS_Application](getcidocumentbody-method-in-class-sms_application) | Gets the configuration item document body. |
| [GetCIDocuments Method in Class SMS_Application](getcidocuments-method-in-class-sms_application) | Gets all of the configuration item documents for the application installation. |
| [InitiateUserInstall Method in Class SMS_Application](initiateuserinstall-method-in-class-sms_application) | **Warning:** This method is reserved for future use. |
| [ManageDeploymentForDevice Method in Class SMS_Application](managedeploymentfordevice-method-in-class-sms_application) | **Warning:** This method is reserved for future use. |
| [Restore Method in Class SMS_Application](restore-method-in-class-sms_application) | Restores this application and related deployment type as a current active application. |
| [SetIsExpired Method in Class SMS_Application](setisexpired-method-in-class-sms_application) | Sets the expired status of this application. |
| [UpdateStats Method in Class SMS_Application](updatestats-method-in-class-sms_application) | Updates the statistics for this application. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, sizelimit]

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

If any of the contained deployment type of dependent deployment types is user context, this application is user context.

| Value | Execution context |
| --- | --- |
| 0 | System |
| 1 | User |

`Featured` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

If the application is marked as a featured application, this will be 1. The default value is 0.

`HasContent` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this application has content; otherwise, `false`.

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsDeployable` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the application can be deployed; otherwise, `false`. The application can be deployed if it contains an enabled deployment type.

`IsDeployed` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the application has been deployed to client; otherwise, `false`. An application is deployed if there is assignment that assigns this application to any collection.

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

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class)..

`IsSuperseding` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

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

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LogonRequirement` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Requirement for user logon to setup. Possible values are:

| Value | Logon required? |
| --- | --- |
| 0 | Others |
| 1 | LogonRequired |

`Manufacturer` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Manufacturer of the application.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`NumberOfDependentDTs` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of deployment types that depend on this application.

`NumberOfDependentTS` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`NumberOfDeployments` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of deployments.

`NumberOfDeploymentTypes` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of deployment types.

`NumberOfDevicesWithApp` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of devices with this application installed.

`NumberOfDevicesWithFailure` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of devices that failed to install this application.

`NumberOfSettings` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of settings that refer to the deployment types for this application.

`NumberOfUsersWithApp` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of users with this application installed.

`NumberOfUsersWithFailure` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of users that failed to install this application.

`NumberOfUsersWithRequest` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of users that requested this application.

`NumberOfVirtualEnvironments` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of virtual environments which refer to the deployment types of this application.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

The package identifier of the content. A unique key, that the user can set, otherwise the system will generate a default identifier. A reference to the same package identifier is in the `SMS_CIContentPackage` class.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

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

Digest XML that defines the application.

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SoftwareVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Software version description

`SourceCIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Source application version if the application is imported.

`SourceModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Source application model name if the application is imported.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time the summarization task was run for this application.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).