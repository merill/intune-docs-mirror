---
layout: Conceptual
title: SMS_OSDeploymentKitInstalledVersion Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentkitinstalledversion-server-wmi-class
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
description: Learn how to represent a mapping of server names to an installed Assessment and Deployment Kit (ADK) version using SMS_OSDeploymentKitInstalledVersion class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d102f64f-491d-85d1-1725-a8db4b3509d3
document_version_independent_id: f352a3cb-b3f8-de7e-2931-81ac53cbd4d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_osdeploymentkitinstalledversion-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_osdeploymentkitinstalledversion-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_osdeploymentkitinstalledversion-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6985eab0-a00d-8382-fff1-33d2dc88d263
---

# SMS_OSDeploymentKitInstalledVersion Class - Configuration Manager | Microsoft Learn

The `SMS_OSDeploymentKitInstalledVersion` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a mapping of server names to an installed Assessment and Deployment Kit (ADK) version.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentKitInstalledVersion : SMS_BaseClass
{
    String DeploymentKitVersion;
    String FQDN;
    UInt32 MachineID;
    String NetBiosName;
};

```

## Methods

The `SMS_OSDeploymentKitInstalledVersion` class does not define any methods.

## Properties

`DeploymentKitVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The version of the deployment kit installed on the computer.

`FQDN` Data type: `String`

Access type: Read/Write

Qualifiers: none

The fully qualified domain name of the computer.

`MachineID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, not\_null]

A unique identifier for the computer.

`NetBiosName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The NetBIOS name of the computer.

## Remarks

Class qualifiers for this class include:

- Dynamic

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).