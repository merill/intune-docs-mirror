---
layout: Conceptual
title: SMS_MDMDeviceEnrollmentManagers Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class
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
description: The SMS_MDMDeviceEnrollmentManagers WMI class represents On-premises Mobile Device Management (MDM) device enrollment managers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7090bcc4-887f-d177-1e17-53079c859d44
document_version_independent_id: ddcb03de-8691-333b-36f1-f1343b23a19e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 29d3c62e-560e-d9ea-98d1-5ececcf2088b
---

# SMS_MDMDeviceEnrollmentManagers Class - Configuration Manager | Microsoft Learn

The `SMS_MDMDeviceEnrollmentManagers` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents On-premises Mobile Device Management (MDM) device enrollment managers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MDMDeviceEnrollmentManagers : SMS_BaseClass
{
    UInt32 ResourceID;
};

```

## Methods

The following table lists the methods in the `SMS_MDMDeviceEnrollmentManagers` class.

| Method | Description |
| --- | --- |
| [InsertMultipleResourceIds Method in Class SMS_MDMDeviceEnrollmentManagers](insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers) | Inserts multiple resource IDs. |
| [RemoveMultipleResourceIds Method in Class SMS_MDMDeviceEnrollmentManagers](removemultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers) | Deletes multiple resource IDs. |

## Properties

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Resource ID.

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