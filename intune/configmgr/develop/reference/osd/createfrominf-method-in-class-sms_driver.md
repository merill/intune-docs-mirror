---
layout: Conceptual
title: CreateFromINF Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver
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
description: Learn how to use the CreateFromINF method to create an SMS_Driver Server WMI class object based on information from the specified Microsoft Windows .inf file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 970929b7-1cb9-00d2-14fc-7cf0ef56c70b
document_version_independent_id: 4ea2871e-091a-1c8b-f758-ad94697045ec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/createfrominf-method-in-class-sms_driver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f1f73b3d-d935-97f7-149b-50f308beaef4
---

# CreateFromINF Method - Configuration Manager | Microsoft Learn

The `CreateFromINF` Windows Management Instrumentation (WMI) class method, in Configuration Manager, creates an [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object based on information from the specified Microsoft Windows .inf file.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 CreateFromINF(
      String DriverPath,
      String INFFile,
      SMS_Driver Driver
);
```

#### Parameters

`DriverPath` Data type: `String`

Qualifiers: [in]

Valid Universal Naming Convention (UNC) network path to the folder that contains the driver contents. For example, \\Servers\Driver\VideoDriver.

`INFFile` Data type: `String`

Qualifiers: [in]

The name of the INF file.

`Driver` Data type: `SMS_Driver`

Qualifiers: [out]

An [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object with a complete driver catalog.

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure. The error values are available in the [SMS_ExtendedStatus Server WMI Class](../misc/sms_extendedstatus-server-wmi-class) error object. For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

Possible error values include, but aren't limited to, the following:

0 Success

13 The driver is invalid

1633 The driver is valid but doesn't support any platforms supported by Configuration Manager.

2 The SMS Provider can't access the network share.

183 The driver has already been imported.

To find out specifics of an error, see the OSDDriverCatalog.log file.

## Remarks

A driver is represented by an information file (INF). The INF file is a text file that specifies the files that need to be present or downloaded for the operating system to run. The information in this type of file provides installation instructions that the Internet Component Download service provided in Microsoft Internet Explorer 3.0 or later uses to install and register software components that are downloaded from the Internet, in addition to any files required by the components.

Note

Your application should create a driver only by calling this method or the [CreateFromOEM Method in Class SMS_Driver](createfromoem-method-in-class-sms_driver). It should never create a driver directly.

This method creates a new [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object.

Once created, the [SMS_Driver Server WMI Class](sms_driver-server-wmi-class)`SDMPackageXML` contains the driver definition XML. To set the display information used by the Configuration Manager console for the driver, you need to set the localization information in the [SMS_Driver Server WMI Class](sms_driver-server-wmi-class)`LocalizedInformation` property. The driver name used by the display from is available in [SMS_Driver Server WMI Class](sms_driver-server-wmi-class)`SDMPackageXML` property XML. For more information, see How to Import a Windows Driver Described by an INF File into Configuration Manager.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).