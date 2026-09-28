---
layout: Conceptual
title: CollectableFileItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/collectablefileitem-client-wmi-class
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
description: In Configuration Manager, the CollectableFileItem class is a client Windows Management Instrumentation class that defines attributes of a file collection rule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8c263c62-fee7-155b-de7e-dfb56f858d9d
document_version_independent_id: d3e5d357-f5b0-ee60-8fac-eb5d55881844
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/collectablefileitem-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/collectablefileitem-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/collectablefileitem-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 34e81548-0451-f3af-82ea-30e2d5088c7f
---

# CollectableFileItem Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the **CollectableFileItem** class is a client Windows Management Instrumentation (WMI) class that defines attributes of a file collection rule. The rule attributes define criteria, such as file name, directory paths, and file size limits. An example is `collect *.mif in %windir% up to 10 KB`.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CollectableFileItem : SMS_FileCollectionAgent_Policy
{
      Boolean ExcludeCompressedEncrypted;
      String FileCollectionActionID;
      String FileItemID;
      String FileSpec;
      UInt32 MaxItemFileSize;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      Boolean ScanSubdirectories;
      String SearchPath;
      UInt32 Timeout;
};
```

## Methods

The `CollectableFileItem` class does not define any methods.

## Properties

`ExcludeCompressedEncrypted` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Flag indicating whether compressed or encrypted files and directories or both should be excluded from the scan. This property value is typically translated into the **FileSystemFile**, **IsCompressed**, and **IsEncrypted** property query value.

`FileCollectionActionID` Data type: `String`

Access type: Read/Write

Qualifiers: None

ID that matches the **FileCollectionActionID** property for an associated [FileCollectionAction Client WMI Class](filecollectionaction-client-wmi-class) object. The Inventory Agent uses this value to find the [CollectableFileItem Client WMI Class](collectablefileitem-client-wmi-class) class for a particular file collection action.

`FileItemID` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

Unique ID for a **CollectableFileItem** object.

`FileSpec` Data type: `String`

Access type: Read/Write

Qualifiers: None

File mask, including wildcards, used to specify file names that should be collected, for example, Virussig.dat, Boot\*.ini, and \*.mif.

`MaxItemFileSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Total size, in bytes, allowed for files collected under this rule. For example, collect files up to a total of 128 KB for this rule.

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy.

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy instance.

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Precedence for the policy.

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the rule used to create the policy.

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Source of the policy.

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Version of the policy.

`ScanSubdirectories` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Flag indicating whether the file scan should scan subdirectories or only scan the root directory specified by **SearchPath**. This property value is used to format the **FileSystemFilePath** property query value, such as, c:\\\* vs. c:\\.

`SearchPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Root directory of the scan, for example, c:\, %*windir*%, and d:\myapplication\. This property is translated into the **FileSystemFilePath** property value.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Timeout value, in milliseconds. If a **FileSystemFile** query initiated by the Inventory Agent during a file collection scan runs longer than the specified timeout value, the query is canceled. The default value is 7,200,000 milliseconds.

## Remarks

The Inventory Agent uses each instance of this class to build a **FileSystemFile** query and collects the files matching the rule attributes. This class is similar to **InventoryDataItem**, although the properties are less directly translated into a WQL statement. However, the item properties are used to format the specific **FileSystemFile** query for the rule and are then used to identify files matching the attribute criteria. These matching files are then attached to the generated collected file report.

Each **CollectableFileItem** instance contains a reference to a **FileCollectionAction** instance; multiple **CollectableFileItem** rules are used to build the combined collected file report for a single **FileCollectionAction** instance.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).