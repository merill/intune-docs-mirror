---
layout: Conceptual
title: SMS_OSDeploymentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentconfig-server-wmi-class
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
description: Learn how to represent all OSD-related constants and settings with their ADK-specific values using SMS_OSDeploymentConfig class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1493ac28-3e98-1e31-e6a9-7f4278b6b7c0
document_version_independent_id: 9da6e546-f8ff-7367-5f55-288280394c94
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_osdeploymentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_osdeploymentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_osdeploymentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e340a10-abf5-01ad-82b2-60a15e705fb3
---

# SMS_OSDeploymentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_OSDeploymentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents all OSD-related constants and settings with their ADK-specific values.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentConfig : SMS_BaseClass
{
    String DeploymentKitVersion;
    String DeploymentPropertyName;
    String DeploymentPropertyValue;
};

```

## Methods

The `SMS_OSDeploymentConfig` class does not define any methods.

## Properties

`DeploymentKitVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key, not\_null]

The version of the deployment kit with which this property is associated.

`DeploymentPropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: [key, not\_null]

The name of the property.

`DeploymentPropertyValue` Data type: `String`

Access type: Read/Write

Qualifiers: none

The value of the property.

## Remarks

Class qualifiers for this class include:

- Dynamic

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).