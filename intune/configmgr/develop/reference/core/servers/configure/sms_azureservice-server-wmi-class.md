---
layout: Conceptual
title: SMS_AzureService class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_azureservice-server-wmi-class
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
description: The SMS_AzureService WMI class is an SMS Provider server class in Configuration Manager, that represents a Microsoft Azure service that is a cloud distribution point for Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 274e9932-d208-f071-b1c0-00e40b741002
document_version_independent_id: 24d4c9b0-c2e8-ebb7-daba-f4db41ff903b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_azureservice-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_azureservice-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_azureservice-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: dd38955e-e225-ee9d-5a7b-5430db795f62
---

# SMS_AzureService class - Configuration Manager | Microsoft Learn

The `SMS_AzureService` WMI class is an SMS Provider server class in Configuration Manager, that represents a Microsoft Azure service that is a cloud distribution point for Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AzureService : SMS_BaseClass
{
    UInt32 AzureServiceID;
    String DeploymentSlot;
    String Description;
    UInt32 Flags;
    String Fqdn;
    String ManagementCertificate;
    UInt32 ManagementCertificateType;
    String ManagementThumbprint;
    String NALPath;
    String Name;
    UInt32 NumberOfInstances;
    String Region;
    String ServiceCertificate;
    String ServiceCName;
    String ServiceThumbprint;
    String ServiceThumbprintAlgorithm;
    String ServiceType;
    String SiteCode;
    UInt32 State;
    UInt32 StatusDetails;
    UInt32 StorageCriticalThreshold;
    Boolean StorageQuotaGrow;
    UInt32 StorageQuotaInGB;
    String StorageServiceName;
    UInt32 StorageUsage;
    UInt32 StorageWarningThreshold;
    String SubscriptionID;
    UInt32 TrafficCriticalThreshold;
    UInt32 TrafficOutInGB;
    Boolean TrafficOutStopService;
    UInt32 TrafficOutUsage;
    UInt32 TrafficWarningThreshold;
};
```

## Methods

The following table lists the methods in the `SMS_AzureService` class.

| Method | Description |
| --- | --- |
| [Start Method in Class SMS_AzureService](start-method-in-class-sms_azureservice) | Method used to start a Microsoft Azure service (in this case the cloud distribution point). |
| [Stop Method in Class SMS_AzureService](stop-method-in-class-sms_azureservice) | Method used to stop a Microsoft Azure service (in this case the cloud distribution point). |

## Properties

`AzureServiceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, not\_null]

Identifier of the Microsoft Azure service.

`DeploymentSlot` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Deployment slot. Possible values are:

| Value |
| --- |
| Production |
| Staging |

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Description of the Microsoft Azure service.

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits]

Flags for configuring the Microsoft Azure service. Possible values are:

| Value |
| --- |
| WAD\_LOGS\_DONT\_DELETE(0) |

`Fqdn` Data type: `String`

Access type: Read/Write

Qualifiers: none

The concatenation of the property "Name" with ".cloudapp.net".

`ManagementCertificate` Data type: `String`

Access type: Read/Write

Qualifiers: none

Management certificate.

`ManagementCertificateType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Management certificate type. Possible values are:

| Value | Management certificate type |
| --- | --- |
| 0 | PAIR |
| 1 | PUBLICONLY |

`ManagementThumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: none

Management thumbprint.

`NALPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

NAL path for the corresponding Distribution Point.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Name of the Microsoft Azure service based on restrictions imposed by Microsoft Azure.

`NumberOfInstances` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Number of instances to deploy.

`Region` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

This is the value selected from the list of regions eligible for your Microsoft Azure subscription ID, obtained either by using the Configuration Manager Administrator console or the Microsoft Azure management console.

`ServiceCertificate` Data type: `String`

Access type: Read/Write

Qualifiers: none

Service certificate.

`ServiceCName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Should be the same as the CName on the `ServiceCertificate` property.

`ServiceThumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: none

Service certificate thumbprint algorithm supported by Microsoft Azure. The only thumbprint algorithm supported is SHA1.

`ServiceThumbprintAlgorithm` Data type: `String`

Access type: Read/Write

Qualifiers: none

Service certificate thumbprint algorithm supported by Microsoft Azure. Possible values below:

| Thumbprint Algorithm |
| --- |
| SHA1 |

`ServiceType` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Type of Microsoft Azure service. Possible values below:

| Windows Azure Service |
| --- |
| CloudDistributionPoint |

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Site code of the primary site.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Current state.

`StatusDetails` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Current status details.

`StorageCriticalThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the threshold percent at which critical alerts will be generated for storage.

`StorageQuotaGrow` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if Indicates whether storage quota should automatically grow dynamically.

This property isn't currently used.

`StorageQuotaInGB` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Storage quota in gigabytes.

`StorageServiceName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Name of Microsoft Azure storage service, based on restrictions imposed on by Microsoft Azure.

`StorageUsage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the storage usage of the Microsoft Azure storage service in gigabytes.

`StorageWarningThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the threshold percent at which warning alerts will be generated for storage.

`SubscriptionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Subscription identifier of the Microsoft Azure service.

`TrafficCriticalThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the threshold percent at which critical alerts will be generated for traffic out.

`TrafficOutInGB` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Traffic out in gigabytes.

`TrafficOutStopService` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

Indicates whether the service should be stopped when the traffic out threshold is met.

This property isn't currently used.

`TrafficOutUsage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the traffic out usage.

`TrafficWarningThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the threshold percent at which warning alerts will be generated for traffic out.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).