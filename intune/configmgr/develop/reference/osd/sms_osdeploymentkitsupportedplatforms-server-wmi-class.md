---
layout: Conceptual
title: SMS_OSDeploymentKitSupportedPlatforms Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentkitsupportedplatforms-server-wmi-class
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
description: In Configuration Manager, the SMS_OSDeploymentKitSupportedPlatforms Windows Management Instrumentation class is an SMS Provider server class that maps Assessment and Deployment Kit versions to supported platforms.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6a4db978-abfc-5133-7d93-b9ade8d1d4b6
document_version_independent_id: 11dd8a45-b51d-af0b-ce63-829c9b46febc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_osdeploymentkitsupportedplatforms-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_osdeploymentkitsupportedplatforms-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_osdeploymentkitsupportedplatforms-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 77e48988-9a64-5439-bcf5-13ca214c6b30
---

# SMS_OSDeploymentKitSupportedPlatforms Class - Configuration Manager | Microsoft Learn

The `SMS_OSDeploymentKitSupportedPlatforms` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps Assessment and Deployment Kit (ADK) versions to supported platforms.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentKitSupportedPlatforms : SMS_SupportedPlatformsOfflineServicing
{
    String DeploymentKitVersion;
    String Name;
    String OsVersionBuild;
    String ProductType;
};

```

## Methods

The `SMS_OSDeploymentKitSupportedPlatforms` class does not define any methods.

## Properties

`DeploymentKitVersion` Data type: `String`

Access type: Read

Qualifiers: [not\_null]

The version of the deployment kit with which this property is associated.

`Name` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

See [SMS_SupportedPlatformsOfflineServicing Server WMI Class](../core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

`OsVersionBuild` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

See [SMS_SupportedPlatformsOfflineServicing Server WMI Class](../core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

`ProductType` Data type: `String`

Access type: Read

Qualifiers: [key, not\_null]

See [SMS_SupportedPlatformsOfflineServicing Server WMI Class](../core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).