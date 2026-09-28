---
layout: Conceptual
title: SMS_CI_ComplianceSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ci_compliancesummary-server-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn about the simplified syntax, methods, properties, and requirements of the SMS_CI_ComplianceSummary server class.
locale: en-us
document_id: 95c251f8-a289-2010-eb1c-2e2ea5e7f8e7
document_version_independent_id: 6845f902-20d3-ae95-e52e-ba37f2c5803a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_ci_compliancesummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_ci_compliancesummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_ci_compliancesummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a333ee9e-bd3e-a912-d62e-83595324cd75
---

# SMS_CI_ComplianceSummary Class - Configuration Manager | Microsoft Learn

The `SMS_CI_ComplianceSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a compliance summary for a baseline configuration item.

## Syntax

```
Class SMS_CI_ComplianceSummary : SMS_BaseClass
{
      UInt32 ActivatedCount;
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CountCompliant;
      UInt32 CountNoncompliant;
      UInt32 CountTargeted;
      UInt32 FailureCount;
      DateTime LastSummaryTime;
      String ModelName;
      UInt32 Severity;
};
```

## Methods

The `SMS_CI_ComplianceSummary` class does not define any methods.

## Properties

`ActivatedCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that evaluate the configuration item.

`CI_ID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The unique ID of the configuration item. This ID is unique only for the site.

`CI_UniqueID` Data type: `String`

Access type: Read

Qualifiers: [unique]

The unique ID of the configuration item. This ID is unique across sites.

`CountCompliant` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers with which the configuration item is compliant.

`CountNoncompliant` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers with which the configuration item is not compliant.

`CountTargeted` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that are targeted for the configuration item.

`FailureCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that fail to evaluate the configuration item.

`LastSummaryTime` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time when the summary task was last run.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model Name of the configuration item.

`Severity` Data type: `UInt32`

Access type: Read

Qualifiers: None

The noncompliance severity reported by the client for the configuration item.

## Remarks

Class qualifiers for this class include:

- Read (read-only)
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class for compliance monitoring for a configuration item.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).