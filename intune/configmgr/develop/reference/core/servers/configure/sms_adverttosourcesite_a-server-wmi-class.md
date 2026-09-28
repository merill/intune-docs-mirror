---
layout: Conceptual
title: SMS_AdvertToSourceSite_a Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adverttosourcesite_a-server-wmi-class
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
description: Learn how to relate an SMS Advertisement Server class object with the SMS Site Server class object that created the advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 993fdc88-a986-5518-d706-a0dd77992963
document_version_independent_id: b02d8b7b-ecc5-ed98-4221-b585d16aa04a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_adverttosourcesite_a-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_adverttosourcesite_a-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_adverttosourcesite_a-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b8f8e4e9-8005-6fe4-08d1-82eb82a37a30
---

# SMS_AdvertToSourceSite_a Class - Configuration Manager | Microsoft Learn

The `SMS_AdvertToSourceSite_a` association Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class) object with the [SMS_Site Server WMI Class](sms_site-server-wmi-class) object that created the advertisement.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AdvertToSourceSite_a : SMS_BaseAssociation
{
   ref:SMS_Site advertSourceSite;
      ref:SMS_Advertisement ownedAdvert;
};
```

## Methods

The `SMS_AdvertToSourceSite_a` class does not define any methods.

## Properties

`advertSourceSite` Data type: `ref:MS_Site`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Site Server WMI Class](sms_site-server-wmi-class) object path.

`ownedAdvert` Data type: `ref:SMS_Advertisement`

Access type: Read/Write

Qualifiers: [key]

Reference to an [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class) object path.

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