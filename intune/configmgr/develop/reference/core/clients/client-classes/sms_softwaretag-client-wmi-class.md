---
layout: Conceptual
title: SMS_SoftwareTag Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwaretag-client-wmi-class
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
description: Learn how to use SMS_SoftwareTag class to indicate the presence of a software application on a computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fcb1323a-dec3-d5c5-72ec-8a9dcbc43e45
document_version_independent_id: f010730f-4478-76bd-72a5-a0cfd264ce98
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwaretag-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_softwaretag-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_softwaretag-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 51cbae0a-af93-8b9c-1570-b6d31f1b0ad2
---

# SMS_SoftwareTag Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareTag` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that indicates the presence of a software application on a computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareTag
{
      String DisplayVersion;
      Boolean EntitlementRequired;
      String ProductName;
      String SoftwareCreator;
      String SoftwareCreatorRegid;
      String SoftwareLicensor;
      String SoftwareLicensorRegid;
      String TagCreator;
      String TagCreatorRegid;
      String UniqueID;
      SInt32 VersionMajor;
      SInt32 VersionMinor;
};
```

## Methods

The `SMS_SoftwareTag` class does not define any methods.

## Properties

`DisplayVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Display version.

`EntitlementRequired` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the software application requires a license entitlement grant from the software publisher prior to usage.

`ProductName` Data type: `String`

Access type: Read-only

Qualifiers: None

Product name used as a display name used in reports.

`SoftwareCreator` Data type: `String`

Access type: Read-only

Qualifiers: None

Software creator.

`SoftwareCreatorRegid` Data type: `String`

Access type: Read-only

Qualifiers: None

Registration identifier of the software creator.

`SoftwareLicensor` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Software licensor.

`SoftwareLicensorRegid` Data type: `String`

Access type: Read-only

Qualifiers: None

Registration identifier of the software licensor.

`TagCreator` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Tag creator.

`TagCreatorRegid` Data type: `String`

Access type: Read-only

Qualifiers: key

Registration identifier of the tag creator.

`UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: key

Unique identier.

`VersionMajor` Data type: `SInt32`

Access type: Read-only

Qualifiers: None

Major version of the software.

`VersionMinor` Data type: `SInt32`

Access type: Read-only

Qualifiers: None

Minor version of the software.

## Remarks

Note

This class is not currently used to support existing Asset Intelligence reports. However, it can be enabled to support custom reports.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).