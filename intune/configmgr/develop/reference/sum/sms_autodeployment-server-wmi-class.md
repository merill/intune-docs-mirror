---
layout: Conceptual
title: SMS_AutoDeployment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_autodeployment-server-wmi-class
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
description: Learn how to use Configuration Manager SMS_AutoDeployment Windows Management Instrumentation (WMI) class to represent an automatic deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a696936a-dbd0-6cc8-4b58-f9556ed50b89
document_version_independent_id: 017d43c0-730c-0fce-7f1d-55a47ebb61e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_autodeployment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_autodeployment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_autodeployment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 61e71c15-c7a4-a809-e7f8-981c2537f4b9
---

# SMS_AutoDeployment Class - Configuration Manager | Microsoft Learn

The `SMS_AutoDeployment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an automatic deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AutoDeployment :  SMS_BaseClass
{
    Boolean AutoDeploymentEnabled;
    SInt32 AutoDeploymentID;
    String AutoDeploymentProperties;
    String CollectionID;
    String ContentTemplate;
    String Description;
    String DeploymentTemplate;
    Boolean IsServicingPlan;
    SInt32 LastErrorCode;
    DateTime LastErrorTime;
    DateTime LastRunTime;
    UInt32 LocaleID;
    String Name;
    String Schedule;
    String UpdateRuleXML;
};

```

## Methods

The following table lists the methods in the `SMS_AutoDeployment` class.

| Method | Description |
| --- | --- |
| [EvaluateAllAutoDeployment Method in Class SMS_AutoDeployment](evaluateallautodeployment-method-in-class-sms_autodeployment) | Evaluates all automatic deployments. |
| [EvaluateAutoDeployment Method in Class SMS_AutoDeployment](evaluateautodeployment-method-in-class-sms_autodeployment) | Evaluates an automatic deployment. |

## Properties

`AutoDeploymentEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Specifies whether the automatic deployment is enabled. The default value is `true`.

`AutoDeploymentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

The automatic deployment ID.

`AutoDeploymentProperties` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, lazy]

Automatic deployment properties in XML format.

`CollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The ID of the target collection. This value is needed as a security key.

`ContentTemplate` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, lazy]

The content template XML for the automatic deployment.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

A description for the automatic deployment.

`DeploymentTemplate` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, lazy]

The deployment template XML for the automatic deployment.

`IsServicingPlan` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Specifies whether the automatic deployment rule is a servicing plan. The default value is `true`.

`LastErrorCode` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The last error encountered when processing the automatic deployment rule failed. The default value is 0.

`LastErrorTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time that an error was encountered.

`LastRunTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The last time that the automatic deployment was processed.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The locale of the automatic deployment name or description fields.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Name for the automatic deployment.

`Schedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule for the automatic deployment.

`UpdateRuleXML` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, lazy]

Update rule XML for the automatic deployment.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).