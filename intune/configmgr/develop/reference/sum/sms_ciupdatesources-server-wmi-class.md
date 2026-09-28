---
layout: Conceptual
title: SMS_CIUpdateSources Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class
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
description: Provides information on all the update sources associated with an [SMS_SoftwareUpdate Server WMI Class]
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 12560809-adf3-f511-fd04-d6d70738fd59
document_version_independent_id: d6216bec-9c57-a0eb-4c88-8eb1b69608a1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6b5d1b49-1a58-51a8-5bf7-fa8305e020cf
---

# SMS_CIUpdateSources Class - Configuration Manager | Microsoft Learn

The `SMS_CIUpdateSources` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides information on all the update sources associated with an [SMS_SoftwareUpdate Server WMI Class](sms_softwareupdate-server-wmi-class) object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIUpdateSources : SMS_BaseClass
{
    UInt32 CI_ID;
    DateTime DateCreated;
    DateTime DateModified;
    UInt32 MinSourceVersion;
    String ModelName;
    UInt32 UpdateSource_ID;
};
```

## Methods

The `SMS_CIUpdateSources` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the configuration item corresponding to the software update. This ID is unique only for the site. The ID is defined by the `CI_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

`DateCreated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the configuration was created.

`DateModified` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The last date and time when the configuration item was modified.

`MinSourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Minimum version of the source in which the update was found.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`UpdateSource_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The ID of the software update source. Supported sources are Windows Server Update Services (WSUS) and ITMU/Offline Catalog. For more information, see [SMS_SoftwareUpdateSource Server WMI Class](sms_softwareupdatesource-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class in synchronizing software update metadata so that correct information can be obtained from a source during software update deployment.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).