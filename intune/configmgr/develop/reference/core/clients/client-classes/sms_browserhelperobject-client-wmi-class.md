---
layout: Conceptual
title: SMS_BrowserHelperObject Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_browserhelperobject-client-wmi-class
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
description: In Configuration Manager, the SMS_BrowserHelperObject class is a client Windows Management Instrumentation class  that enumerates all browser helper objects on a computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 70192764-84f1-9854-1b3c-de18ffc6b39e
document_version_independent_id: 2e00a7a1-5c79-7d7b-9243-75b93184359d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_browserhelperobject-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_browserhelperobject-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_browserhelperobject-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bfc5cb9c-b14a-a2ac-5d9d-cd61de3c25a5
---

# SMS_BrowserHelperObject Class - Configuration Manager | Microsoft Learn

The `SMS_BrowserHelperObject` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that enumerates all browser helper objects on a computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BrowserHelperObject
{
      String BinFileVersion;
      String BinProductVersion;
      String CLSID;
      String Description;
      String FileName;
      String FilePropertiesHash;
      String FilePropertiesHashEx;
      String FileVersion;
      String Product;
      String ProductVersion;
      String Publisher;
      String Version;
};
```

## Methods

The `SMS_BrowserHelperObject` class does not define any methods.

## Properties

`BinFileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`BinProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`CLSID` Data type: `String`

Access type: Read-only

Qualifiers: None

The COM class ID that is associated with the browser helper object.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: None

File description that can be presented to users, for example, "Groove Shell Extensions Module".

`FileName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the file, including the extension but excluding the path, for example, "GrooveShellExtensions.dll".

`FilePropertiesHash` Data type: `String`

Access type: Read-only

Qualifiers: [key]

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, and `FileName` properties of the file.

`FilePropertiesHashEx` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, `FileName`, `FileVersion`, `BinProductVersion`, and `BinFileVersion` properties of the file.

`FileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the file, for example, "12.0.4518.1014".

`Product` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the product with which the file is distributed, for example, "Microsoft Windows".

`ProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the product with which the file is distributed, for example, "4.2.0.2623".

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: None

The company that produced the file, for example, "Microsoft Corporation" or "Standard Microsystems Corporation, Inc.".

`Version` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

## Remarks

Many users install applications from the Web unintentionally or through various deceptive practices. Browser helper objects allow extensions to the Internet Explorer browser. These extensions typically appear as toolbars in the user interface. Most software that is considered malware is in this form.

This class enumerates all the subkeys of HKEY\_LOCAL\_MACHINE\Software\Microsoft\Windows\CurrentVersion\Explorer\Browser Helper Objects, gathering a set of class identifiers that are used to retrieve useful information from a second lookup in the HKEY\_CLASSES\_ROOT\CLSID\[retrieved bho id]\InprocServer32 hive. Enumeration of the subkeys provides a list of the binaries from which the header information can be retrieved.

Note

When constructing the `FilePropertiesHash` property, if the header data for the executable file is `null` for the company, product, or version field, the file name in uppercase is substituted for the field.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).