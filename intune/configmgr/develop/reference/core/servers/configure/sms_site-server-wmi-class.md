---
layout: Conceptual
title: SMS_Site Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class
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
description: An SMS Provider server class that represents identification and status data for a Configuration Manager site installation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 383b3cbe-ada3-8a3d-0a03-485dfa369cba
document_version_independent_id: f2951d5e-cbd1-9c0f-f94c-1c4ba1770421
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 1f2c2a1b-bd77-e016-a9bd-45e87af1382f
---

# SMS_Site Class - Configuration Manager | Microsoft Learn

The `SMS_Site` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents identification and status data for a Configuration Manager site installation.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Site : SMS_BaseClass
{
      UInt32 BuildNumber;
      String Features;
      String InstallDir;
      UInt32 Mode;
      String ReportingSiteCode;
      UInt32 RequestedStatus;
      UInt32 SecondarySiteCMUpdateStatus;
      String ServerName;
      String SiteCode;
      String SiteName;
      UInt32 Status;
      String TimeZoneInfo;
      UInt32 Type;
      String Version;
};
```

## Methods

The following table shows the methods in the `SMS_Site` class.

| Method | Description |
| --- | --- |
| [EncryptDataEx Method in Class SMS_Site](encryptdataex-method-in-class-sms_site) | Encrypts data using the specified site server's public key and returns the encrypted data. |
| [GetAutoUpgradeConfigs Method in Class SMS_Site](getautoupgradeconfigs-method-in-class-sms_site) | Gets configurations for autoupgrade settings. |
| [GetClientInfo Method in Class SMS_Site](getclientinfo-method-in-class-sms_site) | Gets information about a client. |
| [GetClientPilotingConfigs Method in Class SMS_Site](getclientpilotingconfigs-method-in-class-sms_site) | Gets the configurations for client piloting settings. |
| [GetFeatureState Method in Class SMS_Site](getfeaturestate-method-in-class-sms_site) | Gets the enabled/disabled state of a feature. |
| [GetSiteADInfo Method in Class SMS_Site](getsiteadinfo-method-in-class-sms_site) | Gets Active Directory information of site server. |
| [ImportGlobalUserAccount Method in Class SMS_Site](importglobaluseraccount-method-in-class-sms_site) | Encrypts data that is shared in the hierarchy. |
| [ImportGlobalUserAccountEx Method in Class SMS_Site](importglobaluseraccountex-method-in-class-sms_site) | Encrypts data that is shared in the hierarchy. |
| [ImportMachineEntry Method in Class SMS_Site](importmachineentry-method-in-class-sms_site) | Imports computer information. |
| [IsUsedCert Method in Class SMS_Site](isusedcert-method-in-class-sms_site) | Determines whether the specified certificate is used. |
| [RedistributeAutoUpgradeClientContent Method in Class SMS_Site](redistributeautoupgradeclientcontent-method-in-class-sms_site) | Redistributes autoupgrade client content to the specified distribution point. |
| [SubmitRegistrationRecord Method in Class SMS_Site](submitregistrationrecord-method-in-class-sms_site) | Submits a registration record. |
| [UpdateAutoUpgradeClientContent Method in Class SMS_Site](updateautoupgradeclientcontent-method-in-class-sms_site) | Updates autoupgrade client content to all distribution points. |
| [UpdateAutoUpgradeConfigs Method in Class SMS_Site](updateautoupgradeconfigs-method-in-class-sms_site) | Updates configurations for autoupgrade settings. |
| [UpdateClientPilotingConfigs Method in Class SMS_Site](updateclientpilotingconfigs-method-in-class-sms_site) | Updates the configurations for client piloting settings. |
| [UpdateConsoleUsageData Method in Class SMS_Site](updateconsoleusagedata-method-in-class-sms_site) | Updates console usage data received from console connections. |
| [UpdateFeatureState Method in Class SMS_Site](updatefeaturestate-method-in-class-sms_site) | Updates the enabled/disabled state of a feature. |
| [VerifyNoLoops Method in Class SMS_Site](verifynoloops-method-in-class-sms_site) | Determines whether the parent-child relationship for a given site results in a recursive loop. |

## Properties

`BuildNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Configuration Manager build number. The default value is 0.

`Features` Data type: `String`

Access type: Read/Write

Qualifiers: None

Reserved for internal use.

`InstallDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory in which Configuration Manager was installed. The default value is "".

`Mode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Mode of the site. Possible values are:

| Value | Site mode |
| --- | --- |
| 1 | Replication maintenance. |
| 2 | Recovery in progress. |
| 3 | Upgrade in progress. |
| 4 | Evaluation has expired. |
| 5 | Site expansion in progress. |
| 6 | Interop mode where there are primary sites, having the same version as the CAS, weren't upgraded. |
| 7 | Interop mode where there are secondary sites, having the same version as the top-level site server, weren't upgraded. |

`ReportingSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

Site code for the parent of the current site. The default value is "".

`RequestedStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Value indicating a request for secondary site status. Possible values are listed below. The default value is 1001.

| Value | Requested site status |
| --- | --- |
| 1001 | Create a secondary site; the primary site will send down the installation media. |
| 1002 | Create a secondary site using the installation media already available on the secondary site. |
| 1003 | Secondary site creation has started. |
| 1004 | Upgrade a secondary site; the primary site will send down the installation media. |
| 1005 | Upgrade a secondary site using the installation media already available on the secondary site. |
| 1006 | Secondary site upgrade has started. |
| 1007 | Deinstall a secondary site. |
| 1008 | Secondary site deinstall has started. |
| 1009 | Delete a secondary site. |
| 1010 | Secondary site deletion has started. |
| 1011 | Recover a secondary site; the primary site will send down the installation media. |
| 1012 | Recover a secondary site; the installation media is already available on the secondary site. |
| 1013 | Secondary site recovery has started. |

Use this property for creating and upgrading a secondary site. Only values preceded by "SEC\_REQUEST\_" can be set.

`SecondarySiteCMUpdateStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Indicates whether the secondary site server has the latest Configuration Manager updates installed from its parent.

`ServerName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Server name of the site on which Configuration Manager is installed. The default value is "".

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

Three-letter site code for the site. The default value is "".

`SiteName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the site. The default value is "".

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

Current status of the site. Possible values are listed below. The default value is ACTIVE (1).

| Value | Site status |
| --- | --- |
| 1 | ACTIVE |
| 2 | PENDING |
| 3 | FAILED |
| 4 | DELETED |
| 5 | UPGRADE |
| 6 | Failed to delete or deinstall the secondary site. |
| 7 | Failed to upgrade the secondary site. |
| 8 | Secondary site recovery is in progress. |
| 9 | Failed to recover secondary site. |

`TimeZoneInfo` Data type: `String`

Access type: Read/Write

Qualifiers: None

Site server time zone represented as a Win32 `TIME_ZONE_INFORMATION` structure that is retrieved by the Win32 `GetTimeZoneInformation` function. The default value is "".

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Type of site. Possible values are listed below. The default value is SECONDARY (1).

| Value | Site type |
| --- | --- |
| 1 | SECONDARY |
| 2 | PRIMARY |
| 4 | CAS |

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

Complete Configuration Manager version of the current site. The default value is "".

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    `SMS_Site` can be used to get the site server name from a known site code. For an example, see [How to Create a PXE Service Point Role](../../../../osd/how-to-enable-a-pxe-service-point-role).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).