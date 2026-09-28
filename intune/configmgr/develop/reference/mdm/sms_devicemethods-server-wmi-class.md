---
layout: Conceptual
title: SMS_DeviceMethods Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class
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
description: The SMS_DeviceMethods WMI class is an SMS Provider server class that provides access to actions that you can take on mobile devices and Microsoft Exchange ActiveSync devices.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4510d46c-0b65-157b-3fda-b8047b195f80
document_version_independent_id: 7ec26d43-b38d-7dc5-4074-c3ddc69ee1b7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/390894b2-8646-4f7e-b8cd-2209156272a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12b23b77-ab37-4318-a036-4f6690586386
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 31676e7f-7680-93e9-8c4b-bce83e577bae
---

# SMS_DeviceMethods Class - Configuration Manager | Microsoft Learn

The `SMS_DeviceMethods` Windows Management Instrumentation (WMI) class is an SMS Provider server class that provides access to actions that you can take on mobile devices and Microsoft Exchange ActiveSync devices.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceMethods : SMS_Baseclass ();
```

## Methods

The following table shows the methods in `SMS_DeviceMethods`.

| Method | Description |
| --- | --- |
| [AllowAccess Method in Class SMS_DeviceMethods](allowaccess-method-in-class-sms_devicemethods) | Lets the Exchange ActiveSync device connect to Exchange. |
| [BlockAccess Method in Class SMS_DeviceMethods](blockaccess-method-in-class-sms_devicemethods) | Blocks the Exchange ActiveSync device from accessing to Exchange. |
| [NEW SP1: CancelRetire Method in Class SMS_DeviceMethods](cancelretire-method-in-class-sms_devicemethods) | Cancels the retirement of this device from Configuration Manager. |
| [CancelWipe Method in Class SMS_DeviceMethods](cancelwipe-method-in-class-sms_devicemethods) | Cancels a pending wipe request on mobile devices or Exchange ActiveSync devices. |
| [NEW SP1: RequestRetire Method in Class SMS_DeviceMethods](requestretire-method-in-class-sms_devicemethods) | Retires this device from Configuration Manager. |
| [RequestWipe Method in Class SMS_DeviceMethods](requestwipe-method-in-class-sms_devicemethods) | Removes Microsoft Exchange and Configuration Manager software from the mobile device or Exchange ActiveSync device. |

## Properties

The `SMS_DeviceMethods` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Mobile device setting packages use programs, distribution points, and advertisements to collections to distribute their content.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).