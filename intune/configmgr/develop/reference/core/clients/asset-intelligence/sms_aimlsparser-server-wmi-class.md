---
layout: Conceptual
title: SMS_AIMLSParser Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class
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
description: In Configuration Manager, the SMS_AIMLSParser Windows Management Instrumentation class imports license data.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7d9c873f-b6e3-461d-4292-a9240f4efd49
document_version_independent_id: 52d3be71-474a-53b7-d889-73e687c36f48
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 5af65375-b68e-9bf1-2bfe-baa3f38429a1
---

# SMS_AIMLSParser Class - Configuration Manager | Microsoft Learn

The `SMS_AIMLSParser` Windows Management Instrumentation (WMI) class in Configuration Manager imports license data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AIMLSParser : SMS_BaseClass ();
```

## Methods

The following table lists the methods in the `SMS_AIMLSParser` class.

| Method | Description |
| --- | --- |
| [GetStatus Method in Class SMS_AIMLSParser](getstatus-method-in-class-sms_aimlsparser) | Monitors the status of a previous call to the `Import` method. The returned values of the `Status` parameter are: 0 - Successful completion |
| [GetSummary Method in Class SMS_AIMLSParser](getsummary-method-in-class-sms_aimlsparser) | Retrieves the counts of imported Microsoft license count and non-Microsoft license count. |
| [Import Method in Class SMS_AIMLSParser](import-method-in-class-sms_aimlsparser) | Imports the MLS statement as specified by the `MLSFilepath` parameter (in UNC format) into the Configuration Manager database. |

## Properties

The `SMS_AIMLSParser` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- DisplayName("AI Hinv Classes List")
- Dynamic
- Provider("ExtnProv")
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).