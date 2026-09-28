---
layout: Conceptual
title: SMS_ExtendedStatus class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class
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
description: The technical details of the SMS_ExtendedStatus server WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 20b0a705-1316-4b2d-0a72-eabcac97bdb0
document_version_independent_id: db03646c-3fda-f08e-346b-f56609eaabc3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_extendedstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 2e739bc2-eaac-c48a-3640-8867c285a7c2
---

# SMS_ExtendedStatus class - Configuration Manager | Microsoft Learn

The `SMS_ExtendedStatus` WMI class in Configuration Manager supports an error object that supplies the cause and nature of the current error.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ExtendedStatus : __ExtendedStatus
{
     String CauseInfo;
     String Description;
     UInt32 ErrorCode;
     String File;
     UInt32 Line;
     String ObjectInfo;
     String Operation;
     String ParameterInfo;
     String ProviderName;
     String SQLMessage;
     UInt32 SQLSeverity;
     UInt32 SQLStatus;
     UInt32 StatusCode;
};
```

## Methods

The `SMS_ExtendedStatus` class does not define any methods.

## Properties

`CauseInfo` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional error information. This property can contain the reason the error occurred, along with other information. For example, Software Product Compliance sets this property to the field number that caused the error.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional detailed description of an error or an operational status.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Composite error code that defines the severity, facility, action, object, and reason for the error. The Ssperrcode.h header file contains macros to evaluate the error condition. The following table lists the five-bit field masks that make up this property. The default value is 0.

| Mask | Description |
| --- | --- |
| Severity (bits 31-30) | Value that identifies whether the application can continue and to what extent it can continue. The three levels of severity are functional, minor, and major. A functional error allows an application to continue with any aspect of Configuration Manager. A minor error allows an application to continue with other areas of Configuration Manager that are not related to the area that caused this error. If the application receives a major error, however, it should stop processing requests and terminate. |
| Facility (bits 27-22) | The facility that was being accessed when the error occurred, for example, internal, file, Structured Query Language (SQL), or security. |
| Action (bits 21-16) | The action that failed, for example, open, read, or persist. |
| Object (bits 15-8) | The type of object against which the action was being performed, for example, a parameter or an instance. |
| Reason (bits 7-0) | The reason for the failure. This value might not be set. For example, R\_PDFERROR is set if an error occurred while loading a package definition file (.pdf). |

`File` Data type: `String`

Access type: Read/Write

Qualifiers: None

Module that raised the error condition. The default value is "".

`Line` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Line number inside the module where the error was raised. The default value is 0.

`ObjectInfo` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional error information that contains the object that caused the error, the parameter that caused the error, or the Structured Query Language (SQL) message text, along with other data. For example, Software Product Compliance sets this property to the number of the record that caused the error.

`Operation` Data type: `String`

Access type: Read/Write

Qualifiers: None

Operation taking place at the time of the failure or anomaly.

`ParameterInfo` Data type: `String`

Access type: Read/Write

Qualifiers: None

One or more parameters involved in the error or status change.

`ProviderName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the provider that caused or reported the error or status change. If a provider was not involved, this string is set to "Windows Management".

`SQLMessage` Data type: `String`

Access type: Read/Write

Qualifiers: None

Error message text of the last SQL Server error. This property is set to `null` if no SQL Server error is present.

`SQLSeverity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Severity code of the last SQL Server error. This property is set to `null` if no SQL Server error is present.

`SQLStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Error code of the last SQL Server error. This property is set to `null` if no SQL Server error is present.

`StatusCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Error or information code for an operation.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

    For information about how to use this class, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).