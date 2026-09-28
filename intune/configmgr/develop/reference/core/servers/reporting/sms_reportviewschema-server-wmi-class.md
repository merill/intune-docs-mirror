---
layout: Conceptual
title: SMS_ReportViewSchema Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class
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
description: An SMS Provider server class that represents the views and columns available for building a report.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 97ce5a24-7ddc-69ad-414c-26e7054e3ec1
document_version_independent_id: ea25e42f-19fc-5c00-f4d1-da7bba186972
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7485c665-f6c2-8401-2553-f31b83995b1d
---

# SMS_ReportViewSchema Class - Configuration Manager | Microsoft Learn

The `SMS_ReportViewSchema` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the views and columns that are available for building a report.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ReportViewSchema : SMS_BaseClass
{
      Boolean IsStringType;
      String ViewColumnName;
      String ViewName;
};
```

## Methods

The following table shows the methods in `SMS_ReportViewSchema`.

| Method | Description |
| --- | --- |
| [GetSampleValues Method in Class SMS_ReportViewSchema](getsamplevalues-method-in-class-sms_reportviewschema) | Gets sample values for a report view schema. |

## Properties

`IsStringType` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the values of the column are strings.

`ViewColumnName` Data type: `String`

Access type: Read Only

Qualifiers: [key]

Name of a column in the view.

`ViewName` Data type: `String`

Access type: Read Only

Qualifiers: [key]

Name of a view.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).