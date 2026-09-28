---
layout: Conceptual
title: ValidateQuery Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery
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
description: Learn how to verify that the query collection rule is a valid WQL or Extended WQL statement using ValidateQuery class method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 939317b4-da25-080e-0f62-cbfdf8eff16e
document_version_independent_id: d900586d-b76a-16b1-0eef-bf774986d46a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 45661118-5d60-dc03-df00-c7d9d56cb124
---

# ValidateQuery Method - Configuration Manager | Microsoft Learn

The `ValidateQuery` Windows Management Instrumentation (WMI) class method, in Configuration Manager, verifies that the query collection rule is a valid WQL or Extended WQL statement.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
Boolean ValidateQuery(
     String WQLQuery
);
```

#### Parameters

`WQLQuery` Data type: `String`

Qualifiers: [in]

Query statement to validate.

## Return Values

A `Boolean` data type that is `true` if the query is validated.

## Remarks

Your application calls this method before adding a query rule to a collection. An invalid query rule results in no members being added to the collection for that query. This can be misleading and hard to debug.

In addition to being syntactically correct, the query rule must specify resource class names in the FROM clause. For example, the FROM clause must specify [SMS_R_System Server WMI Class](../manage/sms_r_system-server-wmi-class), [SMS_R_User Server WMI Class](../manage/sms_r_user-server-wmi-class), [SMS_R_UserGroup Server WMI Class](../manage/sms_r_usergroup-server-wmi-class), or a user-defined resource class name.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).