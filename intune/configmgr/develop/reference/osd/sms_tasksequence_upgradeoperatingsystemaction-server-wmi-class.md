---
layout: Conceptual
title: SMS_TaskSequence_UpgradeOperatingSystemAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_upgradeoperatingsystemaction-server-wmi-class
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
description: Details of the SMS_TaskSequence_UpgradeOperatingSystemAction server WMI class.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5ec421eb-b5ad-038e-a9b5-e42f2e06c8d0
document_version_independent_id: 38ba5e5d-6ce1-3cf9-f95c-7ebb642dc4fe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_upgradeoperatingsystemaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_upgradeoperatingsystemaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_upgradeoperatingsystemaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: a02860ae-2ffb-ddff-1351-9ae1f084809b
---

# SMS_TaskSequence_UpgradeOperatingSystemAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_UpgradeOperatingSystemAction` WMI class is an SMS provider server class in Configuration Manager. It represents a task sequence action that upgrades the OS. This step is only supported for Windows 10 and Windows 11.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_UpgradeOperatingSystemAction : SMS_TaskSequence_Action
{
    SMS_TaskSequence_Condition Condition;
    Boolean ContinueOnError;
    String Description;
    String DriverPackageID;
    String DynamicUpdateSettings;
    Boolean Enabled;
    String FeatureUpdateAssignmentId;
    String FeatureUpdateName
    Boolean IgnoreMessages;
    UInt32 InstallEditionIndex;
    String InstallPackageID;
    String InstallPath;
    String Name;
    String OsProductKey;
    String PreserveSettings;
    Boolean ScanOnly;
    UInt32 SetupTimeout;
    String StagedContent;
    String SupportedEnvironment;
    UInt32 Timeout;
};
```

## Methods

The `SMS_TaskSequence_UpgradeOperatingSystemAction` class doesn't define any methods.

## Properties

### `Condition`

Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `DriverPackageID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[TaskSequencePackage]`

The package ID of the driver package to use during upgrade.

### `DynamicUpdateSettings`

Data type: `string`

Access type: Read/Write

Qualifiers: `[ValueMap]`

Specifies whether to dynamically update Windows Setup with Windows Update.

Possible values:

- `Disable`
- `OveridePolicy`

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `FeatureUpdateAssignmentId`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The deployment ID of a feature update used to upgrade the Window OS.

### `FeatureUpdateName`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of a feature update used to upgrade the Window OS.

### `IgnoreMessages`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Ignores compatibility messages that can be dismissed. The default value is `false`.

### `InstallEditionIndex`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The installation edition index. The default value is `1`.

### `InstallPackageID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[TaskSequencePackage("image"), RequiredIfNull("InstallPath")]`

The ID of the OS upgrade package to use.

### `InstallPath`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNull("InstallPackageID")]`

The path or environment variable to the OS upgrade package to use.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `OsProductKey`

Data type: `String`

Access type: Read/Write

Qualifiers: `[QuasiSecret]`

The product key for the OS upgrade content.

### `PreserveSettings`

Data type: `String`

Access type: Read/Write

Qualifiers: `[ValueMap]`

Specifies what data to keep during an upgrade. The default value is `Upgrade`, which keeps applications, data, and settings. For best results, use the default value.

### `ScanOnly`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Runs a Windows Setup compatibility scan without starting the upgrade. The default value is `false`.

### `SetupTimeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The timeout that applies when running Windows Setup from the command line during an upgrade.

### `StagedContent`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The path or environment variable to the driver content to use for the upgrade.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The default value is `FullOS`. For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).