---
layout: Conceptual
title: SMS_SummarizerStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerstatus-server-wmi-class
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
description: Learn how the SMS_SummarizerStatus class is an SMS Provider server class that identifies registered summarizers, without defining any specific status information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5bccfcfd-37ba-a189-165e-252a91e966e4
document_version_independent_id: 969d3319-5395-93d6-de24-27a239e00993
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_summarizerstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_summarizerstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 55a0e196-a8ec-a81d-08e8-44b463f32b58
---

# SMS_SummarizerStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SummarizerStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that identifies registered summarizers, without defining any specific status information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizerStatus : SMS_BaseClass
{
      String GUID_ID;
      String MessageDLL;
      UInt32 MessageID;
      String SiteCode;
      UInt32 Status;
      DateTime Updated;
};
```

## Methods

The `SMS_SummarizerStatus` class does not define any methods.

## Properties

`GUID_ID` Data type: `String`

Access type: Read

Qualifiers: [key]

GUID under which the summarizer is registered in the registry.

`MessageDLL` Data type: `String`

Access type: Read

Qualifiers: None

Resource DLL containing the localized name of the summarizer.

`MessageID` Data type: `String`

Access type: Read

Qualifiers: None

ID the string resource in the `MessageDLL` property that contains the localized name of the summarizer.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key]

Site code of the Configuration Manager site.

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating the health of the data associated with the registered summarizer. Possible values are:

| Value | Status |
| --- | --- |
| GREEN(0) | OK. There are no warning or error messages. |
| YELLOW(1) | Warning. Warning messages were generated, but error messages were not generated. This status also indicates that the storage objects are approaching their threshold. |
| RED(2) | Critical. There are error messages, or the storage objects have exceeded their thresholds. |

`Updated` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time when the registration was last updated.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).