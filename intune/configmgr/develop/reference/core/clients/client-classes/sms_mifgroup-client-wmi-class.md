---
layout: Conceptual
title: SMS_MIFGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_mifgroup-client-wmi-class
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
description: A client Windows Management Instrumentation class that serves as a dynamic instance provider class allowing WMI reporting of Management Information Format files that extend the client inventory.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 21161239-e532-d7bd-dab1-88bcc2b02d45
document_version_independent_id: 3065974f-38e3-10fc-abf2-0f20172f648b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_mifgroup-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_mifgroup-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_mifgroup-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b28cdca-9e11-9837-73ef-2f1c4150bff6
---

# SMS_MIFGroup Class - Configuration Manager | Microsoft Learn

The `SMS_MifGroup` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that serves as a dynamic instance provider class allowing WMI reporting of Management Information Format (MIF) files that extend the client inventory.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class
{
      String ArchitectureName;
      String ComponentName;
      String MIFGroupVerbatim;
      String MIFClassVerbatim;
      String MIFKeysVerbatim;
      String AttributeKeyValues;
      String MIFAttributesVerbatim[];
      String MIFFile;
      UInt64 MIFFileSize;
      String MIFDirectory;
};
```

## Properties

`ArchitectureName` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Architecture of the component and MIF groups. The default value is System.

`ComponentName` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Component for MIF groups. The default value is Workstation.

`MIFGroupVerbatim` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Group name in MIF syntax, for example, Name = \hotfix\.

`MIFClassVerbatim` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Class name in MIF syntax, for example, Class = \MICROSOFT|UPDATE|1.0\.

`MIFKeysVerbatim` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Reported key values, based on attribute IDs, in MIF syntax, for example, key = 1, 2.

`AttributeKeyValues` Data type: **String**

Access type: Read-only

Qualifiers: [key]

Attribute key values, concatenated in string format, corresponding to the key attribute IDs. This property is primarily useful as a WMI instance key for MIF groups. It is not especially useful for MIF group translation.

`MIFAttributesVerbatim` Data type: **String** array

Access type: Read-only

Qualifiers: None

Array of MIF attribute definitions and values in MIF syntax.

`MIFFile` Data type: **String**

Access type: Read-only

Qualifiers: None

MIF file name queried, typically \*.mif.

`MIFFileSize` Data type: **UInt64**

Access type: Read-only

Qualifiers: None

Size of the MIF file containing the group. This property is used to limit reporting based on the MIF file size.

`MIFDirectory` Data type: **String**

Access type: Read-only

Qualifiers: None

Not implemented. MIF directory queried.

## Remarks

This class is used by the Inventory Client Agent to enumerate the third-party MIF files at a designated collection directory. For each file, the instance provider parses the file against the MIF syntax, validates the contents against Configuration Manager restrictions, and reports each individual MIF group in a generic form that is usable by the Inventory Client Agent and management point. The generic instance format is specifically designed to translate consistently and easily between MIF syntax for any number of MIF group definitions and values. This translation is especially important on the management point, where the Inventory Client Agent report is translated back into MIF format for processing at the Configuration Manager site server.

The preferred way to extend client inventory is through WMI instances (static or dynamic). However, this provider allows a migration step for SMS 2.0 MIF files already in use.

The `SMS_MIFGroup` class is specifically used to expose No Identification MIF files (NOIDMIFs) through WMI in client inventory. NOIDMIFs are used to extend client inventory beyond that requested for specific WMI instances in the site policy (see InventoryDataItem). For example, hardware vendors can supply asset information by using NOIDMIFs.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).