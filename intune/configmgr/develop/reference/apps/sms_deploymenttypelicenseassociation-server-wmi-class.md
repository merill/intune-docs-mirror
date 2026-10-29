---
layout: Conceptual
title: SMS_DeploymentTypeLicenseAssociation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class
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
description: Learn about the simplified syntax, methods, properties, and requirements of the SMS_DeploymentTypeLicenseAssociation server class.
locale: en-us
document_id: c92f19dd-ca02-2c66-4463-3b2a45c0a4df
document_version_independent_id: 0b288412-e5d3-045b-37b3-ed564659b9fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b3d6be29-2e8a-9aa0-bbb2-fc49079ba78d
---

# SMS_DeploymentTypeLicenseAssociation Class - Configuration Manager | Microsoft Learn

The `SMS_DeploymentTypeLicenseAssociation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a license association for a deployment type.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeploymentTypeLicenseAssociation : SMS_BaseClass
{
    UInt32 ID;
    String LicenseID;
    String DTModelName;
    Boolean IsEnabled;
};

```

## Methods

The following table lists the methods in the `SMS_DeploymentTypeLicenseAssociation` class.

| Method | Description |
| --- | --- |
| [AddLicense Method in Class SMS_DeploymentTypeLicenseAssociation](addlicense-method-in-class-sms_deploymenttypelicenseassociation) | Adds license information to an application deployment type. |

## Properties

`ID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The ID of the deployment type.

`LicenseID` Data type: `String`

Access type: Read

Qualifiers: none

The ID of the license.

`DTModelName` Data type: `String`

Access type: Read

Qualifiers: none

The deployment type model name.

`IsEnabled` Data type: `Boolean`

Access type: Read

Qualifiers: none

Indicates whether the association is enabled.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).