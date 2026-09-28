---
layout: Conceptual
title: SMS_TaskSequence_ApplyDriverPackageAction class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applydriverpackageaction-server-wmi-class
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
description: The SMS Provider server class represents an action used in a task sequence to make all device drivers in a driver package available for use by Windows setup.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 065df257-8faf-8531-477b-29aaec60bdf9
document_version_independent_id: 4ea0ad3e-0faf-b73f-f13f-71383a3d22b7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_applydriverpackageaction-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_applydriverpackageaction-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_applydriverpackageaction-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2ac9edd1-81fb-8530-8d0b-301393e5ca19
---

# SMS_TaskSequence_ApplyDriverPackageAction class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_ApplyDriverPackageAction` WMI class is an SMS Provider server class in Configuration Manager. It represents an action used in a task sequence to make all device drivers in a driver package available for use by Windows setup.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_ApplyDriverPackageAction : SMS_TaskSequence_Action
{
        String BootCriticalContentUniqueID;
        String BootCriticalDriverID;
        String BootCriticalHardwareComponent;
        String BootCriticalID;
        String BootCriticalINFFile;
        SMS_TaskSequence_Condition Condition;
        Boolean ContinueOnError;
        String Description;
        String DriverPackageID;
        Boolean Enabled;
        String Name;
        Boolean Recurse;
        String SupportedEnvironment;
        UInt32 Timeout;
        Boolean UnsignedDriver;
};
```

## Methods

The `SMS_TaskSequence_ApplyDriverPackageAction` class doesn't define any methods.

## Properties

### `BootCriticalContentUniqueID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The unique ID of the content associated a boot-critical mass storage device driver. If this ID isn't specified, no mass-storage device driver is installed. The driver content can be obtained from the [SMS_CIToContent server WMI class](../sum/sms_citocontent-server-wmi-class) where the **CI\_ID** property matches the driver ID. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalDriverID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(2)]`

Optional ID specified by the **CI\_UniqueID** property of the [SMS_Driver server WMI class](sms_driver-server-wmi-class) object to install for a boot-critical mass storage device driver. The default value is `null`.

### `BootCriticalHardwareComponent`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

Hardware component used if a boot-critical mass storage device driver is being installed. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The boot-critical ID of the mass-storage device driver to be installed. The default value is `null`. This ID is listed in the "scsi" section of the device driver Txtsetup.oem file.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalINFFile`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The INF file of a boot-critical mass-storage device driver to be installed. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

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

Qualifiers: `[CommandLineArg(1), TaskSequencePackage, Not_Null]`

ID of the driver package to install. This value is indicated by the **PackageID** property of the specific [SMS_DriverPackage server WMI class](sms_driverpackage-server-wmi-class) object.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `Recurse`

Data type: `Boolean`

Access type: Read/write

Values:

- `false` (default): Use the list of drivers from the driver package.
- `true`: Run DISM once to recurse on the entire driver package folder.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

The default value for this class is WinPE.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS_TaskSequence_Action server WMI class](sms_tasksequence_action-server-wmi-class).

### `UnsignedDriver`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[Not_Null, VariableName("OSDAllowUnsignedDriver")]`

Set `true` to configure Windows to allow unsigned device drivers to be installed. The default value is `false`.

Note

This property is required by the action. However, it's deprecated and not used by modern OS versions.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("osddriverclient.exe /install:%1 \<?2:\\"/bootcritical:%%OSDApplyDriverBootCriticalContentUniqueID%%,%%OSDApplyDriverBootCriticalINFFile%%,%%OSDApplyDriverBootCriticalHardwareComponent%%,%%OSDApplyDriverBootCriticalID%%\\">/unsigned:%%OSDAllowUnsignedDriver%%"),ActionCategory{"Drivers,2,6"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyDriverPackageControl", "TaskSequenceOptionControl"}, VariablePrefix("OSDApplyDriver")]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../core/reqs/server-development-requirements).