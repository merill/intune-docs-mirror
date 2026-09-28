---
layout: Conceptual
title: SMS_InstalledSoftwareMS Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedsoftwarems-client-wmi-class
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
description: This SMS_InstalledSoftwareMS class is no longer used in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 43a057b7-81bd-a32e-8b4e-81e6f77ac088
document_version_independent_id: 6833f637-73d2-a580-caa1-b664a0e89b4b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedsoftwarems-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_installedsoftwarems-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_installedsoftwarems-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: b1104769-1be0-e8fd-8f99-5a02c2cbd971
---

# SMS_InstalledSoftwareMS Class - Configuration Manager | Microsoft Learn

Important

This class is no longer used in Configuration Manager.

The `SMS_InstalledSoftwareMS` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that merges Microsoft-specific installed software information from multiple sources to provide categorization and Microsoft Licensing information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InstalledSoftwareMS
{
      String ChannelCode;
      String ChannelID;
      String MPC;
      String ProductCode;
      String SoftwareCode;
};
```

## Methods

The `SMS_InstalledSoftwareMS` class does not define any methods.

## Properties

`ChannelCode` Data type: `String`

Access type: Read-only

Qualifiers: None

The procurement channel for the product. Possible values are:

| Value | Description |
| --- | --- |
| 0 | Full Packaged Product |
| 1 | Compliance Checked Product |
| 2 | OEM |
| 3 | Volume |

`ChannelID` Data type: `String`

Access type: Read-only

Qualifiers: None

Three-digit ID that is also used to indicate the channel as obtained from the `ProductID` property for Microsoft products. The specific values vary by product.

`MPC` Data type: `String`

Access type: Read-only

Qualifiers: None

Unique five-digit Microsoft Product Code that identifies a specific product family, version, language, and target operating system.

`ProductCode` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique code for the particular product release. This code is represented as a GUID for Microsoft Windows Installer based applications or as the string used by the product to register with **Add or Remove Programs**.

`SoftwareCode` Data type: `String`

Access type: Read-only

Qualifiers: [key]

A standardized version of the `ProductCode` property. All characters in the string are lowercase.

## Remarks

This class merges information from as many as five sources. The first source is the Microsoft Windows `MsiEnumProducts` function. This function enumerates through all the products that are currently advertised or installed. Other sources of information for all installed software are the following registry keys:

- HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\[User SID]\Products
- HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

    The class also gathers information for operating system software from the following sources:
- WMI class root\CIMV2:Win32\_OperatingSystem
- Registry key HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).