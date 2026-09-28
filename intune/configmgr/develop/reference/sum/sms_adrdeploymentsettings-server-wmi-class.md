---
layout: Conceptual
title: SMS_ADRDeploymentSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_adrdeploymentsettings-server-wmi-class
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
description: Learn how to represent Automatic Deployment Rule (ADR) deployment settings in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2aa8b76f-fa50-6bae-c1dc-4aff8004b991
document_version_independent_id: 9c785db7-321a-3cfa-a513-29ddc83c4303
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_adrdeploymentsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_adrdeploymentsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_adrdeploymentsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7cca61bc-e991-8a4e-019d-81bddb6008fb
---

# SMS_ADRDeploymentSettings Class - Configuration Manager | Microsoft Learn

The `SMS_ADRDeploymentSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Automatic Deployment Rule (ADR) deployment settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ADRDeploymentSettings : SMS_BaseClass
{
    UInt32 ActionID;
    String AssociatedDeploymentID;
    String CollectionID;
    String CollectionName;
    UInt32 DeploymentNumber;
    String DeploymentTemplate;
    Boolean Enabled;
    UInt32 LocaleID;
    String Name;
    Sint32 RuleID;
};

```

## Methods

The `SMS_ADRDeploymentSettings` class does not define any methods.

## Properties

`ActionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The action ID.

`AssociatedDeploymentID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Deployment ID for the associated deployment.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The collection ID.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Name of collection.

`DeploymentNumber` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The deployment number.

`DeploymentTemplate` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, lazy]

Deployment template XML for the auto deployment.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Specifies whether the deployment is enabled.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Locale of the auto deployment name and description fields.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the deployment setting.

`RuleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

ID for the associated automatic deployment rule.

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