---
layout: Conceptual
title: GetPDFData Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package
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
description: Learn how to produce SMS Package and Program Server class objects from a loaded package with GetPDFData.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1402e0c2-1562-ce99-ef73-d21479bbd50a
document_version_independent_id: f0133c02-04ba-0394-000c-1b181cc62ad4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b083be8-649c-d355-8ccd-37b280a05c2a
---

# GetPDFData Method - Configuration Manager | Microsoft Learn

The `GetPDFData` Windows Management Instrumentation (WMI) class method, in Configuration Manager, produces [SMS_Package Server WMI Class](sms_package-server-wmi-class) and [SMS_Program Server WMI Class](sms_program-server-wmi-class) objects from a loaded package definition file.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetPDFData(
     UInt32 PDFID,
     SMS_Package PackageData,
      SMS_Program ProgramData[]
);
```

#### Parameters

`PDFID` Data type: `UInt32`

Qualifiers: [in]

ID of the package definition file to be retrieved. Get this value from the [SMS_PDF_Package Server WMI Class](sms_pdf_package-server-wmi-class) class.

`PackageData` Data type: `SMS_Package`

Qualifiers: [out]

An [SMS_Package Server WMI Class](sms_package-server-wmi-class) object produced from the package definition file.

`ProgramData` Data type: `SMS_Program` Array

Qualifiers: [out]

[SMS_Program Server WMI Class](sms_program-server-wmi-class) objects produced from the package definition file.

## Return Values

An `SInt32` data type that is one of the following bit-field warning flags.

| Flag | Description |
| --- | --- |
| WARN\_BAD\_RUN (0) | Invalid run information specified. |
| WARN\_BAD\_RESTART (1) | Invalid restart information specified. |
| WARN\_BAD\_CANRUNWHEN (2) | Invalid CanRunWhen information specified. |
| WARN\_BAD\_ASSIGNMENT (3) | Invalid assignment information specified. |
| WARN\_BAD\_DEPENDPROG (4) | Invalid DependentProgram information specified. |
| WARN\_BAD\_SPECIFYDRIVE (5) | Invalid SpecifyDrive information specified. |
| WARN\_BAD\_ESTDISKSPACE (6) | Invalid EstimatedDiskSpace information specified. |
| WARN\_NO\_SUPPCLINFO (7) | No SupportedClients information specified. |
| WARN\_BAD\_SUPPCLINFO (8) | Invalid SupportedClients information specified. |
| WARN\_VER1PDF (9) | Version 1.0 file used. |
| WARN\_REMPRONOUKEY(10) | The remove program is set, but no uninstall Key is given. |

## Example Code

For an example that uses this method, see [How to Create a Package Using a PDF Template](../../../../core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).