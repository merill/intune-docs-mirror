---
layout: Conceptual
title: SMS_CI_ComplianceHistory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ci_compliancehistory-server-wmi-class
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
description: Learn how to use the SMS_CI_ComplianceHistory class in Configuration Manager to get the compliance history for both configuration items and configuration baselines.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a1eaaeab-0ad1-6d6c-423c-70df545a3f62
document_version_independent_id: c0f0a03f-75c3-2492-f2f2-068b0651d665
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_ci_compliancehistory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_ci_compliancehistory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_ci_compliancehistory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 757dd8d3-283c-f3aa-0a5d-c4623075cdf0
---

# SMS_CI_ComplianceHistory Class - Configuration Manager | Microsoft Learn

The `SMS_CI_ComplianceHistory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides the compliance history for both configuration items and configuration baselines.

## Syntax

```
Class SMS_CI_ComplianceHistory : SMS_BaseClass
{
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIVersion;
      DateTime ComplianceEndDate;
      DateTime ComplianceStartDate;
      UInt32 ComplianceValidationRuleFailures;
      UInt32 DesiredState;
      Boolean IsApplicable;
      Boolean IsCompliant;
      Boolean IsDetected;
      UInt32 MaxNoncomplianceCriticality;
      String ModelName;
      UInt32 ResourceID;
      UInt32 SDMPackageVersion;
      String UserName;
};
```

## Methods

The `SMS_CI_ComplianceHistory` class does not define any methods.

## Properties

`CI_ID` Data type: `Uint32`

Access type: Read-only

Qualifiers: [key, read]

The unique ID of the configuration item. This ID is unique only for the site.

`CI_UniqueID` Data type: `String`

Access type: Read

Qualifiers: None

The unique ID of the configuration item. This ID is unique across sites.

`CIVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Version of the configuration item.

`ComplianceEndDate` Data type: `DateTime`

Access type: Read

Qualifiers: None

The end date from which a Configuration Item was compliant, non-compliant or error. See corresponding start date in `ComplianceStartDate`.

`ComplianceStartDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [key, read]

The start date from which a Configuration Item was compliant, non-compliant or error. See corresponding end date in `ComplianceEndDate`.

`ComplianceValidationRuleFailures` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of validation rule failures.

`DesiredState` Data type: `UInt32`

Access type: Read

Qualifiers: None

The resolved state in the context of Applications. Whether the Application was intended to be installed, uninstalled and so on.

`IsApplicable` Data type: `Boolean`

Access type: Read

Qualifiers: None

`true` if the configuration item is applicable on the computer.

`IsCompliant` Data type: `Boolean`

Access type: Read

Qualifiers: None

`true` if the configuration item is compliant on the computer.

`IsDetected` Data type: `Boolean`

Access type: Read

Qualifiers: None

`true` if the configuration item is detected on the computer.

`MaxNoncomplianceCriticality` Data type: `UInt32`

Access type: Read

Qualifiers: None

The maximum noncompliance severity reported by the client for the configuration item.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Model Name of the configuration item.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

The unique ID of the resource for the configuration item.

`SDMPackageVersion` Data type: `UInt32`

Access type: Read

Qualifiers: None

This property is deprecated. in Configuration Manageronly the Configuration Item version is used.

`UserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

User name.

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