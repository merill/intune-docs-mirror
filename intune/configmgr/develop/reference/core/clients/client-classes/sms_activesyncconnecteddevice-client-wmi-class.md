---
layout: Conceptual
title: SMS_ActiveSyncConnectedDevice Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncconnecteddevice-client-wmi-class
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
description: Learn how to represent a device connected to the ActiveSyn service using SMS_ActiveSyncConnectedDevice class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2ef63b30-5984-148d-26e1-635159a01d33
document_version_independent_id: 2fdaec60-e94d-30a9-085e-5645ddc0b14b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncconnecteddevice-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_activesyncconnecteddevice-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncconnecteddevice-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a6b146fb-6079-12db-6160-9d419e98a616
---

# SMS_ActiveSyncConnectedDevice Class - Configuration Manager | Microsoft Learn

The `SMS_ActiveSyncConnectedDevice` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents a device connected to the ActiveSync service.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ActiveSyncConnectedDevice : SMS_Class_Template
{
      String DeviceOEMInfo;
      String DeviceType;
      String InstalledClientID;
      String InstalledClientServer;
      String InstalledClientVersion;
      String LastSyncTime;
      String OS_AdditionalInfo;
      String OS_Build;
      String OS_Major;
      String OS_Minor;
      String OS_Platform;
      String ProcessorArchitecture;
      String ProcessorLevel;
      String ProcessorRevision;
};
```

## Methods

The `SMS_ActiveSyncConnectedDevice` class does not define any methods.

## Properties

`DeviceOEMInfo` Data type: `String`

Access type: Read/Write

Qualifiers:

[SMS\_Report("True"), key]

OEM information for the device.

`DeviceType` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

Type of device.

`InstalledClientID` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

The ID of the installed client.

`InstalledClientServer` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

The ID of the server for the installed client.

`InstalledClientVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

The version of the installed client.

`LastSyncTime` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

The time when the device was last synchronized.

`OS_AdditionalInfo` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

Additional information about the client operating system.

`OS_Build` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True")]

The build associated with the client operating system.

`OS_Major` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The major version number of the operating system.

`OS_Minor` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The minor version number of the operating system.

`OS_Platform` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The platform on which the operating system is running.

`ProcessorArchitecture` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The architecture for the device processor.

`ProcessorLevel` Data type: `String`

Access type: Read/Write

Qualifiers: SMS\_Report("True"), key]

The processor level.

`ProcessorRevision` Data type: `String`

Access type: Read/Write

Qualifiers: [SMS\_Report("True"), key]

The processor revision.

## Remarks

All properties of this class are marked with qualifiers to indicate that they represent items that are generated dynamically (reported) based on the content of the SMS\_def.mof file.