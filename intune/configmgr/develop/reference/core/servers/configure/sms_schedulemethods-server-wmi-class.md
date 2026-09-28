---
layout: Conceptual
title: SMS_ScheduleMethods Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_schedulemethods-server-wmi-class
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
description: Learn how the SMS_ScheduleMethods abstract Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, represents methods for decoding and encoding schedule tokens into and from a Configuration Manager interval string.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 87dab729-44ff-c59e-50ab-3616acbdd779
document_version_independent_id: f9b61a29-031e-4cb5-fcae-1f366a132468
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_schedulemethods-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_schedulemethods-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_schedulemethods-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c1badb5f-85bd-36a9-3e0d-3bbbd85841c5
---

# SMS_ScheduleMethods Class - Configuration Manager | Microsoft Learn

The `SMS_ScheduleMethods` abstract Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents methods for decoding and encoding schedule tokens into and from a Configuration Manager interval string.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ScheduleMethods : SMS_BaseClass
{
};
```

## Methods

The following table shows the methods in `SMS_ScheduleMethods`.

| Method | Description |
| --- | --- |
| [ReadFromString Method in Class SMS_ScheduleMethods](readfromstring-method-in-class-sms_schedulemethods) | Reads `SMS_ScheduleToken` objects from an interval string. |
| [WriteToString Method in Class SMS_ScheduleMethods](writetostring-method-in-class-sms_schedulemethods) | Writes `SMS_ScheduleToken` objects to an interval string. |

## Properties

None.

## Remarks

The methods are used in packing and unpacking a schedule token.

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    A Configuration Manager interval string is an internal representation of a schedule token, represented by an [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class) object. Configuration Manager interval strings aren't of the same format as WMI interval strings.

    This class isn't used to convert schedule tokens to or from the friendly scheduling strings, for example, "Occurs every 1 day(s) effective 9:27AM Tuesday", found in the Configuration Manager console.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).