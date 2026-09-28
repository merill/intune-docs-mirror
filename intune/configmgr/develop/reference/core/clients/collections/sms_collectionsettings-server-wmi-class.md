---
layout: Conceptual
title: SMS_CollectionSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class
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
description: Learn how the SMS_CollectionSettings class is an SMS Provider server class that represents settings for an SMS_Collection Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 16612f32-5756-09dd-fdfe-be6a0b2567cc
document_version_independent_id: 40e268c7-3251-0125-50bc-e535d2bb945c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fb06d71e-11ff-16e8-c0f2-c543ad2b241b
---

# SMS_CollectionSettings Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents settings for an [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object.

## Syntax

```
Class SMS_CollectionSettings : SMS_BaseClass
{
      UInt32 ClusterCount;
      UInt32 ClusterPercentage;
      UInt32 ClusterTimeout;
      String CollectionID;
      UInt32 CollectionVariablePrecedence;
      SMS_CollectionVariable CollectionVariables[];
      DateTime LastModificationTime;
      UInt32 LocaleID;
      UInt32 PollingInterval;
      SMS_PowerConfig PowerConfigs[];
      Boolean PollingIntervalEnabled;
      String PostAction;
      String PreAction;
      UInt32 RebootCountdown;
      Boolean RebootCountdownEnabled;
      UInt32 RebootCountdownFinalWindow;
      SMS_ServiceWindow ServiceWindows[];
      String SourceSite;
      UInt32 UseCluster;
      UInt32 UseClusterPercentage;
};
```

## Methods

The `SMS_CollectionSettings` class does not define any methods.

## Properties

`ClusterCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of computers that can be offline in a cluster. The default value is 1.

`ClusterPercentage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Percent of computers that can be offline in a cluster. The default value is 50.

`ClusterTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Timeout for the scripts. The default value is 600.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key, read]

A unique key that maps to the parent collection. The default value is "".

`CollectionVariablePrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Precedence that is used for conflict resolution. The default value is 1.

`CollectionVariables` Data type: `SMS_CollectionVariable` Array

Access type: Read-only

Qualifiers: [read, lazy]

SMS\_CollectionVariable Server WMI Class objects representing collection variables.

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last modification date and time for collection settings.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Locale ID to use in converting the localized name and description. The default value is 1033 (U.S. English).

You can get the locale for the Configuration Manager installation from the [SMS_Identification Server WMI Class](../../servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

`PostAction` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Windows PowerShell script to run after an update deployment.

`PreAction` Data type: `String`

Access type: Read/Write

Qualifiers: None

The Windows PowerShell script to run before an update deployment.

`PollingInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Policy polling interval, in minutes. The default value is 5.

`PollingIntervalEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the polling interval is enabled. The default value is `false`.

`PowerConfigs` Data type: `SMS_PowerConfig` Array

Access type: Read-only

Qualifiers: [read, lazy]

SMS\_PowerConfig Server WMI Class objects representing the power configuration for a specific collection.

`RebootCountdown` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Reboot countdown. The default value is 5.

`RebootCountdownEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if reboot countdown is enabled. The default value is `false`.

`RebootCountdownFinalWindow` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The point at which the final maintenance window is shown for the reboot countdown. The default value is 5.

`ServiceWindows` Data type: `SMS_ServiceWindow` Array

Access type: Read-only

Qualifiers: [read, lazy]

[SMS_ServiceWindow Server WMI Class](../../servers/configure/sms_servicewindow-server-wmi-class) objects representing maintenance windows that are used for making the collection settings.

`SourceSite` Data type: `String`

Access type: Read Only

Qualifiers: [SizeLimit("3"), Not\_null]

Site code of the source site.

`UseCluster` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

A non-zero value indicates that the collection is being used as a cluster. The default value is 0.

`UseClusterPercentage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether to use the ClusterPercentage property. The default value is 1.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).