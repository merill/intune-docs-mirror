---
layout: Conceptual
title: CreateFromOEM Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver
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
description: Creates a set of mass-storage SMS_Driver Server WMI Class objects referenced by the specified Txtsetup.oem file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f4530285-9cf6-2935-0619-ba253f3b22a8
document_version_independent_id: 4f852acf-9b61-c4bb-f7e5-6b18b60da540
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/createfromoem-method-in-class-sms_driver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 1791c05c-8653-359f-26d6-10fefffcaea7
---

# CreateFromOEM Method - Configuration Manager | Microsoft Learn

The `CreateFromOEM` Windows Management Instrumentation (WMI) class method, in Configuration Manager, creates a set of mass-storage [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) objects referenced by the specified Txtsetup.oem file.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CreateFromOEM(
      String DriverPath,
      String OEMFile,
      SMS_Driver Drivers[]
);
```

#### Parameters

`DriverPath` Data type: `String`

Qualifiers: [in]

Universal Naming Convention (UNC) path containing the driver content.

`OEMFile` Data type: `String`

Qualifiers: [in]

Relative path of the Txtsetup.oem file.

`Drivers` Data type: `SMS_Driver Array`

Qualifiers: [out]

An array of drivers with a complete driver catalog.

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure. The error values are available in the [SMS_ExtendedStatus Server WMI Class](../misc/sms_extendedstatus-server-wmi-class) error object. For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

This method returns successfully if at least one of the files referenced by the Txtsetup.oem file is valid.

Possible error values include, but aren't limited to, the following:

0 Success

13 The Txtsetup.oem file is invalid.

All drivers referenced by the Txtsetup.oem file are invalid.

2 The SMS provider can't access the Txtsetup.oem file.

1633 All drivers referenced by the Txtsetup.oem file are valid but don't support any platforms supported by Configuration Manager.

183 All drivers referenced by the Txtsetup.oem file have already been imported.

All drivers referenced by the Txtsetup.oem file have another type of error. See the OSDDriverCatalog.log file on the provider computer for more information.

## Remarks

To support pre-Windows Vista operating system deployments, Configuration Manager uses boot-critical mass storage device drivers. This type of driver is furnished in the form of a Txtsetup.oem file supplied on a disk. The file contains the following information:

- Hardware components supported by the file
- Files to copy from the distribution disk for each component
- Registry keys and values to create for each component

    A mass storage device driver file must be installed before setup on a pre-Windows Vista operating system deployment.

Note

Your application should create a driver only by calling this method or the [CreateFromINF Method in Class SMS_Driver](createfrominf-method-in-class-sms_driver). It should never create a driver directly.

Your application calls this method with a driver Txtsetup.oem file and file path. The method examines the supplied information and creates an array of new [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) objects, one for each referenced .inf file.

This method generates [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) objects with System Definition Model (SDM) package XML defined, and allows your application to make property changes before they're saved.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).