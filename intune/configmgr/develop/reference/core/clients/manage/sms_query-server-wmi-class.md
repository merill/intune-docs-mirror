---
layout: Conceptual
title: SMS_Query Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class
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
description: The SMS_Query Windows Management Instrumentation (WMI) class is an SMS Provider server class. It serves as a container for predefined queries.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 928b493d-7a78-20d4-074f-0e7c380b4d08
document_version_independent_id: 68065723-40b2-226d-a7c9-9cbc21c68a4c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 40df8519-0bf0-812b-3b59-a18cfed1f2f4
---

# SMS_Query Class - Configuration Manager | Microsoft Learn

The `SMS_Query` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as a container for predefined queries.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Query : SMS_BaseClass
{
   String Comments;
   String Expression;
   String LimitToCollectionID;
   String LocalizedCategoryInstanceNames[];
   String Name;
   String QueryID;
   String ResultAliasNames[];
   String ResultColumnsNames[];
   String TargetClassName;
};
```

## Methods

The following table lists the methods in `SMS_Query`.

| Method | Description |
| --- | --- |
| [CreateCCRs Method in Class SMS_Query](createccrs-method-in-class-sms_query) | Generates client configuration requests (CCRs) for the query. |
| [FindResourceSite Method in Class SMS_Query](findresourcesite-method-in-class-sms_query) | Gets site code information for resources from SQL. |

## Properties

`Comments` Data type: **String**

Access type: Read/Write

Qualifiers: None

Comments to document the query. The default value is "".

`Expression` Data type: **String**

Access type: Read/Write

Qualifiers: None

WMI Query Language (WQL) text for the query. The default value is "".

`LimitToCollectionID` Data type: **String**

Access type: Read/Write

Qualifiers: None

ID of a collection. This ID is used to limit the query results to resources that are members of the collection.

`LocalizedCategoryInstanceNames` Data type: **String** Array

Access type: Read

Qualifiers: None

Localized names of the categories to which the resource belongs.

`Name` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name of the query as shown in the Configuration Manager console. The default value is "".

`QueryID` Data type: **String**

Access type: Read-only

Qualifiers: [read, key]

Unique auto-generated ID for the query.

`ResultAliasNames` Data type: **String** Array

Access type: Read-only

Qualifiers: None

If you specify an alias in the query expression, this array will be filled with the aliases.

`ResultColumnsNames` Data type: **String** Array

Access type: Read-only

Qualifiers: None

If you specify an alias in the query expression, this array will be filled with the resulting alias columns names.

`TargetClassName` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name of the target class, found in the FROM clause of the query. The default value is "".

This name is arbitrary for queries that perform a JOIN operation. The Configuration Manager console uses this property for display purposes to give the user an idea of the data that the query retrieves.

## Remarks

Class qualifiers for this class include:

- Secured
- DisplayName("Query")

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    You can use `SMS_Query` to persist valid queries that can be used later in an application or that can be run from the Configuration Manager console.

    Instances of this class with the `TargetClassName` property set to an [SMS_StatusMessage Server WMI Class](../../servers/manage/sms_statusmessage-server-wmi-class) object appear in the System Status node in the Configuration Manager console. All other instances appear in the Queries node.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).