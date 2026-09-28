---
layout: Conceptual
title: QueryOSDBinaryInjectionStatus Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage
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
description: The QueryOSDBinaryInjectionStatus WMI class method, in Configuration Manager, queries the current status of the injection of operating system deployment binaries into a boot image.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2f631ec6-d396-def2-14e3-ed437314d742
document_version_independent_id: 8734e4f6-1ba0-2e28-c8be-73b5465092a1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6ab1ff01-10bd-9339-1cf6-ed10100fa287
---

# QueryOSDBinaryInjectionStatus Method - Configuration Manager | Microsoft Learn

The `QueryOSDBinaryInjectionStatus` Windows Management Instrumentation (WMI) class method, in Configuration Manager, queries the current status of the injection of operating system deployment binaries into a boot image.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 QueryOSDBinaryInjectionStatus(
     String ContextID,
     UInt32 Status,
     UInt32 Progress,
     UInt32 MaxProgress,
     String ProgressText,
     SInt32 ErrorCode,
     String ExtendedErrorInfo
);
```

#### Parameters

`ContextID` Data type: `String`

Qualifiers: [in]

The ID of the context (index) optionally associated with the status upon import of a boot image. This ID is indicated by the `ContextID` property of [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class).

`Status` Data type: `UInt32`

Qualifiers: [out]

The current status of binary injection. Possible values are:

| Value | Status |
| --- | --- |
| 0 | Complete |
| 1 | In progress |
| 2 | Error |
| 3 | No status |

`Progress` Data type: `UInt32`

Qualifiers: [out]

The progress status indicating the number of the current step in the binary injection operation.

`MaxProgress` Data type: `UInt32`

Qualifiers: [out]

The total number of steps in the binary injection operation.

`ProgressText` Data type: `String`

Qualifiers: [out]

A user-readable string identifying the current progress of the binary injection operation.

`ErrorCode` Data type: `SInt32`

Qualifiers: [out]

A 32-bit error code in case of an error in the binary injection operation. An example of an error code is FILE\_NOT\_FOUND (2). The log file contains error code details.

`ExtendedErrorInfo` Data type: `String`

Qualifiers: [out]

Additional error information if the `ErrorCode` parameter is set to an error code. Currently this parameter is used to report driver file information if the binary injection operation fails to inject the binaries for a particular driver.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

To use the `QueryOSDBinaryInjectionStatus` method, your application must:

1. Establish a connection to the SMS Provider. For more information see, [SMS Provider fundamentals](../../core/understand/sms-provider-fundamentals).
2. Access the [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class) object.
3. Call the [ExportDefaultBootImage Method in Class SMS_BootImagePackage](exportdefaultbootimage-method-in-class-sms_bootimagepackage).
4. Then call `QueryOSDBinaryInjectionStatus` as needed to find out the status of the binary injection operation.
5. Use the values of the `Progress` and `MaxProgress` parameters to determine the percent complete status of the binary injection operation.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).