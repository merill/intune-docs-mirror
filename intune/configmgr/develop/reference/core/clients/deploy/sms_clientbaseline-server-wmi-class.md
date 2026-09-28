---
layout: Conceptual
title: SMS_ClientBaseline Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaseline-server-wmi-class
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
description: In Configuration Manager, the SMS_ClientBaseline WMI class is an SMS Provider server class that represents a client deployment baseline.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e27b6204-fc69-9324-5f61-6b8c2bde2956
document_version_independent_id: bda25c30-bbf7-d766-c922-93f81f8fbf42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaseline-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientbaseline-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaseline-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: db887f9a-2970-1702-5117-2be80c4be74e
---

# SMS_ClientBaseline Class - Configuration Manager | Microsoft Learn

The `SMS_ClientBaseline` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment baseline.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientBaseline: SMS_BaseClass
{
    UInt32 BaselineID;
    String BaselineName;
    UInt32 BaselineType;
    String ClientVersion;
    DateTime LastUpdatedTime;
    String SourceHash;
};

```

## Methods

The `SMS_ClientBaseline` class does not define any methods.

## Properties

`BaselineID` Data type: `uint32`

Access type: Read

Qualifiers: [key]

The client baseline ID.

`BaselineName` Data type: `String`

Access type: Read

Qualifiers: none

The friendly name of the client baseline.

`BaselineType` Data type: `uint32`

Access type: Read

Qualifiers: none

The client baseline type. Possible values are:

| Value | Client baseline type |
| --- | --- |
| 1 | Production |
| 2 | Staging |

`ClientVersion` Data type: `String`

Access type: Read

Qualifiers: none

The client baseline version.

`LastUpdatedTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The last time the client baseline was modified.

`SourceHash` Data type: `String`

Access type: Read

Qualifiers: none

The client baseline source hash.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).