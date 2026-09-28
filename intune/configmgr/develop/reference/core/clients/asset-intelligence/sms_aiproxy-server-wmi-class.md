---
layout: Conceptual
title: SMS_AIProxy Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class
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
description: Details of SMS_AIProxy server WMI class
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4a354d7b-8aee-a5d0-bc1a-d593de48ff4e
document_version_independent_id: 9a1678ab-f68b-e6ea-a22c-6d9efca97fbc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 915612f6-c7f5-6c18-e517-7fa252190522
---

# SMS_AIProxy Class - Configuration Manager | Microsoft Learn

The `SMS_AIProxy` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an Asset Intelligence proxy computer.

Note

This class can be accessed only on the central administration site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AIProxy : SMS_BaseClass
{
      string CatalogWatermark;
      uint32 CategoryChangeCount;
      uint32 CPUChangeCount;
      uint32 HWReqChangeCount;
      datetime LastCatalogUpdateCompletion;
      datetime LastCatalogUpdateRequest;
      uint32 LastSCOReturnCode;
      boolean PeriodicCatalogUpdateEnabled;
      string PeriodicCatalogUpdateSchedule;
      uint32 Port;
      string ProxyCertPath;
      boolean ProxyEnabled;
      string ProxyName;
      uint32 ProxyPollingInterval;
      uint32 ProxyState;
      boolean RelevancyOptOut;
      string SCOURL;
      string SiteCode;
      uint32 SoftwareTitlesChangeCount;
};
```

## Methods

The following table lists the methods in the `SMS_AIProxy` class.

| Method | Description |
| --- | --- |
| [RequestCatalogUpdate Method in Class SMS_AIProxy](requestcatalogupdate-method-in-class-sms_aiproxy) | Initiates a System Center Online (SCO) catalog. |

## Properties

`CatalogWatermark` Data type: `String`

Access type: Read Only

Qualifiers: None

The System Center Online catalog watermark, used for internal purposes. This is the watermark that was obtained during the last successful SCO catalog update. This watermark is sent up to the SCO again to request the next batch of updates.

`CategoryChangeCount` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

An incrementing count of how many times the category catalog from SCO has been changed since this proxy was installed.

`CPUChangeCount` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

An incrementing count of how many times the CPU catalog from SCO has been changed since this proxy was installed.

`HWReqChangeCount` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

An incrementing count of how many times the hardware requirements catalog from SCO has been changed since this proxy was installed.

`LastCatalogUpdateCompletion` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

The last successful completion of an SCO catalog update.

`LastCatalogUpdateRequest` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

Indicates the last time a manually triggered Request Catalog Update was done by the user.

`LastSCOReturnCode` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Last HTTPS return code by SCO.

`PeriodicCatalogUpdateEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the user has enabled periodic catalog updates.

`PeriodicCatalogUpdateSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: None

User-defined schedule of when the SCO catalog updates occur.

`Port` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Secure Sockets Layer (SSL) port to use for SCO connection.

| Type | Value |
| --- | --- |
| Default | 443 |
| Minimum | 1 |
| Maximum | 65535 |

`ProxyCertPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Full Universal Naming Convention (UNC) path of the authentication certificate file.

`ProxyEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the user has enabled the proxy operations.

`ProxyName` Data type: `String`

Access type: Read/Write

Qualifiers: key

Fully qualified domain name (FQDN) name of the proxy computer.

`ProxyPollingInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None)

Polling interval between proxy computer and database, in seconds.

| Type | Value |
| --- | --- |
| Default | 900 (15 Minutes) |
| Minimum | 60 (1 Minute) |
| Maximum | 86400 (24 Hours) |

`ProxyState` Data type: `UInt32`

Access type: Read Only

Qualifiers: Enumeration

Indicates the last SCO communication state. This comes from the proxy to the Asset Intelligence server processor through file replication.

| Value | Definition |
| --- | --- |
| 0 | Not installed |
| 1 | Installed |
| 2 | Bad configuration |
| 3 | Reserved state |
| 4 | Bad certificate |
| 5 | SCO is online |
| 6 | SCO is offline |

`RelevancyOptOut` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the user has opted out of sending relevancy information.

`SCOURL` Data type: `String`

Access type: Read/Write

Qualifiers: None

The URL of the SCO.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

Three-letter site code for the site.

`SoftwareTitlesChangeCount` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

An incrementing count of how many times the software title catalog from SCO has been changed since this proxy was installed.

## Remarks

Class qualifiers for this class include:

- DisplayName("AI Proxy Table")
- Dynamic
- Provider("ExtnProv")
- Secured

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../../../misc/class-and-property-qualifiers).

## Return values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).