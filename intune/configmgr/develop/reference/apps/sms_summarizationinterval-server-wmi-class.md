---
layout: Conceptual
title: SMS_SummarizationInterval Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_summarizationinterval-server-wmi-class
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
description: The SMS_SummarizationInterval WMI class represents the months that have been summarized by a monthly usage summary.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 288eeaee-b583-c482-0e02-22e54170ffbb
document_version_independent_id: aff3c3e6-ab5c-fe1f-c23f-da81dbeebbf4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_summarizationinterval-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_summarizationinterval-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_summarizationinterval-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
platformId: d5c837c1-b1c5-784d-4009-fdb3ddfbcaf5
---

# SMS_SummarizationInterval Class - Configuration Manager | Microsoft Learn

The `SMS_SummarizationInterval` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the months that have been summarized by a monthly usage summary.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizationInterval : SMS_BaseClass
{
      DateTime IntervalStart;
      UInt32 TimeKey;
};
```

## Methods

The `SMS_SummarizationInterval` class does not define any methods.

## Properties

`IntervalStart` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the software metering interval starts.

`TimeKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Key that uniquely identifies the interval, equivalent to 100\*Year+Month.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class is the source for the `TimeKey` property in a monthly usage summary represented by [SMS_MonthlyUsageSummary Server WMI Class](sms_monthlyusagesummary-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).