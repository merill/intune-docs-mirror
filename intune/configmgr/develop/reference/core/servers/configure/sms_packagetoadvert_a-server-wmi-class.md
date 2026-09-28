---
layout: Conceptual
title: SMS_PackageToAdvert_a Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagetoadvert_a-server-wmi-class
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
description: The SMS_PackageToAdvert_a WMI class is an SMS Provider server class that relates an SMS_Advertisement Server WMI Class object to the SMS_Package Server WMI Class object that it advertises.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e0361f30-2e26-183e-3be5-7323af3409fd
document_version_independent_id: 5206e551-18f6-5fef-b2a7-c48c185c384b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagetoadvert_a-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagetoadvert_a-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagetoadvert_a-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7218a85c-4f38-cf13-59b4-f75c4caa6eec
---

# SMS_PackageToAdvert_a Class - Configuration Manager | Microsoft Learn

The `SMS_PackageToAdvert_a` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class) object to the [SMS_Package Server WMI Class](sms_package-server-wmi-class) object that it advertises.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageToAdvert_a : SMS_BaseAssociation
{
      ref:SMS_Advertisement advert;
      ref:SMS_Package package;
};
```

## Methods

The `SMS_PackageToAdvert_a` class does not define any methods.

## Properties

`advert` Data type: `ref:SMS_Advertisement`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class) object path.

`package` Data type: `ref:SMS_Package`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Package Server WMI Class](sms_package-server-wmi-class) object path.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).