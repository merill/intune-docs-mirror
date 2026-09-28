---
layout: Conceptual
title: SMS_CIAssignmentToCI Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmenttoci-server-wmi-class
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
description: An SMS Provider server class that represents a relationship between a configuration baseline and its assignments.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 315c7f53-e6a9-9600-9f02-d1f447e2561b
document_version_independent_id: d80a5eed-5770-c148-2c98-0305616c79f6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_ciassignmenttoci-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_ciassignmenttoci-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_ciassignmenttoci-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7b7799b1-301d-d3d0-55ea-512a7aaeb6ef
---

# SMS_CIAssignmentToCI Class - Configuration Manager | Microsoft Learn

The `SMS_CIAssignmentToCI` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a relationship between a configuration baseline and its assignments.

## Syntax

```
Class SMS_CIAssignmentToCI : SMS_BaseClass
{
      UInt32 AssignmentID;
      UInt32 CI_ID;
};
```

## Methods

The `SMS_CIAssignmentToCI` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only.

Qualifiers: [key]

Unique ID of the assignment.

`CI_ID` Data type: `UInt32`

Access type: Read-only.

Qualifiers: [key]

The unique ID of the configuration item. This ID is unique only for the site.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).