---
layout: Conceptual
title: SMS_DCMDeploymentNonCompliantStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantstatus-server-wmi-class
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
description: An SMS Provider server class that represents non-compliant status for a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c8d3f744-2b66-c61d-c98b-e83c3bd9c79d
document_version_independent_id: 3ae08343-1ec9-f1d6-4249-38c558f61daf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_dcmdeploymentnoncompliantstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b77f221c-d8ae-e097-97be-a64f1e950dd4
---

# SMS_DCMDeploymentNonCompliantStatus Class - Configuration Manager | Microsoft Learn

The `SMS_DCMDeploymentNonCompliantStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents non-compliant status for a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentNonCompliantStatus : SMS_BaseClass
{
    UInt32 Assets;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    DateTime DeploymentTime;
    Boolean IsBaselineRule;
    UInt32 Revision;
    UInt32 Rule_ID;
    String RuleDescription;
    String RuleName;
    UInt32 RuleSeverity;
    String RuleStateDisplay;
    UInt32 RuleSubState;
    UInt32 StatusType;
    DateTime SummarizationTime;
    UInt32 SummaryType;
    String TargetCollectionID;
    String ValidationRule;
};
```

## Methods

The `SMS_DCMDeploymentNonCompliantStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Number of assets related to the status.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLRevision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CIName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Deployment time.

`IsBaselineRule` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleSeverity` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Severity of the rule.

`RuleStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleSubState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Rule sub-status type. .

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Summarization time.

`SummaryType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Summary type.

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ValidationRule` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).