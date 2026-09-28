---
layout: Conceptual
title: FileCollectionAction Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/filecollectionaction-client-wmi-class
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
description: A client Windows Management Instrumentation class that associates a set of file collection rules with reporting details, tying together files to collect with the destination of the report.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a8b4645c-f674-4664-d5eb-f882e2edb6f9
document_version_independent_id: 3f475035-1d20-5205-4036-32cb6c15dbb4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/filecollectionaction-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/filecollectionaction-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/filecollectionaction-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ca14b2c2-baee-7c15-3f6e-2005907de1e8
---

# FileCollectionAction Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the **FileCollectionAction** class is a client Windows Management Instrumentation (WMI) class that associates a set of file collection rules with reporting details, tying together files to collect with the destination of the report.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class FileCollectionAction : SMS_FileCollectionAgent_Policy
{
      String CollectionType;
      UInt32 DefaultTimeout;
      Boolean DeleteFilesAfterCollection;
      String Description;
      String FileCollectionActionID;
      String FileDestination;
      String FileType;
      UInt32 MaxTotalFileSize;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      Boolean ReportFileDetails;
      UInt32 ReportTimeout;
      UInt32 ScanInterval;
      String SkipScan;
};
```

## Methods

The `FileCollectionAction` class does not define any methods.

## Properties

`CollectionType` Data type: `String`

Access type: Read/Write

Qualifiers: None

Type of file collection report. The possible values are:

| Value | Description |
| --- | --- |
| Full | Report contains all files collected by the associated **CollectableFileItem** queries. |
| Delta | Report contains files that have changed since the last report. |
| Resync | Report contains files in full report and also contains all files collected, but it is triggered by a site policy resynchronization request. |

`DefaultTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Timeout value, in milliseconds, for each file system inventory provider query executed. The default value is 7,200,000 milliseconds.

`DeleteFilesAfterCollection` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Value used to indicate whether collected files should be deleted from the client after collection.

For IDMIF collection, this value is `true`. The collection results are similar to moving the files from the client to the destination.

For software file collection, this value is `false`. The collection results are similar to copying the files from the client to the destination.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Text field that describes the file collection action. The predefined description values are File Collection and IDMIF Collection.

`FileCollectionActionID` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

Unique ID for the file collection action. Possible values are:

| File Collection Action ID type | Value |
| --- | --- |
| Software File Collection | {00000000-0000-0000-0000-000000000010} |
| IDMIF Collection | {00000000-0000-0000-0000-000000000012} |

`FileDestination` Data type: `String`

Access type: Read/Write

Qualifiers: None

Destination address for the generated report.

`FileType` Data type: `String`

Access type: Read/Write

Qualifiers: None

Type of collected file attachments for a report. Possible values are:

- FILECOLL
- IDMIF

    `MaxTotalFileSize` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Cumulative maximum size of collected files in a generated report. The Inventory Agent ensures that the overall file attachment size does not exceed this value.

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

    Qualifiers: Key

    Unique ID of the rule used to create the policy.

    `PolicySource` Data type: `String`

    Access type: Read/Write

    Qualifiers: [key]

    Source of the policy.

    `PolicyVersion` Data type: `String`

    Access type: Read/Write

    Qualifiers: [key]

    Version of the policy.

    `ReportFileDetails` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: None

    `true` to include external file details for each file attachment in the generated report for software file collection. The generated report contains the original file name, path, size, and modified date.

    `ReportTimeout` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Timeout value used by the client framework for expiring the inventory report (message) sent by the Inventory Agent to the management point. If the inventory report cannot be sent to the management point, the client framework continues to hold on to the message until the report timeout interval. It periodically tries to resend the message.

    `ScanInterval` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Delay, in milliseconds, to pass to the file system inventory provider for the file collection scan.

    `SkipScan` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    File name used to prevent the scanning of a directory. This value is typically set to Skpswi.dat for software file collection. It is typically not set for IDMIF collection.

## Remarks

This class is similar to the **InventoryAction**, with the main difference being the type of collection files for file collection and WMI instances for inventory.

Two predefined file collection actions are provided through the site policy: software file collection and IDMIF collection. For each of these file collection actions, the Inventory Agent generates a report with attachments, based on queries built from **CollectableFileItem** instances. The generated report is sent to the specified destination.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).