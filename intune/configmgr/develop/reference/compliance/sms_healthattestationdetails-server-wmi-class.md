---
layout: Conceptual
title: SMS_HealthAttestationDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_healthattestationdetails-server-wmi-class
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
description: The SMS_HealthAttestationDetails Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that represents Health Attestation details.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d9ccd5b9-32b8-e740-675c-3e1ec86835e2
document_version_independent_id: 35fa377f-0815-0554-c27c-fd02be7528b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_healthattestationdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_healthattestationdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_healthattestationdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 36f0af39-607e-2e91-04fd-b20d6dd73592
---

# SMS_HealthAttestationDetails Class - Configuration Manager | Microsoft Learn

The `SMS_HealthAttestationDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Health Attestation details.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_HealthAttestationDetails : SMS_BaseClass
{
     UInt32 AIKPresent;
     SInt32 BitlockerStatus;
     UInt32 BootDebuggingEnabled;
     UIt32 CertRetrievalStatus;
     UInt32 CodeIntegrityEnabled;
     DateTime DateIssued;
     UInt64 DEPPolicy;
     UInt32 DeviceItemKey;
     UInt32 ELAMDriverLoaded;
     UInt32 HASSupported;
     UInt32 OSKernelDebuggingEnabled;
     UInt32 SafeMode;
     UInt32 SecureBootEnabled;
     UInt32 TestSigningEnabled;
     UInt32 VSMEnabled;
     UInt32 WinPE;
};

```

## Methods

The `SMS_HealthAttestationDetails` class does not define any methods.

## Properties

`AIKPresent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether the Windows Automated Installation Kit (Windows AIK) is present.

`BitlockerStatus` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The status of BitLocker.

`BootDebuggingEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether boot debugging is enabled.

`CertRetrievalStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The status of the certificate retrieval.

`CodeIntegrityEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether code integrity is enabled.

`DateIssued` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The date and time that the certificate was issued.

`DEPPolicy` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

The Apple Device Enrollment Program (DEP) policy.

`DeviceItemKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

The device key.

`ELAMDriverLoaded` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether the Early-Launch Anti-Malware (ELAM) driver is loaded.

`HASSupported` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether health attestation is supported.

`OSKernelDebuggingEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether operating system kernel debugging is enabled.

`SafeMode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

`SecureBootEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether secure boot is enabled.

`TestSigningEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether test-signing is enabled.

`VSMEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether VSM is enabled.

`WinPE` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).