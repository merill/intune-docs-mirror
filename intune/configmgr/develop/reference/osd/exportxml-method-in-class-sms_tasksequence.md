---
layout: Conceptual
title: ExportXml Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how the ExportXml Method exports task sequence XML in a format that is suitable to use on another site.
locale: en-us
document_id: 0a7691ad-e119-b74a-8bc1-7be0075a71a4
document_version_independent_id: 2d82fdca-3bc5-89ce-f6b5-29b8aa0ae363
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 96a80bef-7adb-e0d3-b05b-33a315923223
---

# ExportXml Method - Configuration Manager | Microsoft Learn

The `ExportXml` Windows Management Instrumentation(WMI) class method, in Configuration Manager, exports task sequence XML in a format that is suitable to use on another site.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
String ExportXml(
      String Xml
);
```

#### Parameters

`Xml` Data type: `String`

Qualifiers: [in]

The task sequence XML. This XML comes from a previous call to the [SaveToXml Method in Class SMS_TaskSequence](savetoxml-method-in-class-sms_tasksequence).

## Return Values

A `String` data type defining the exported task sequence XML.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Important

Your application must use secure techniques when calling the [SaveToXml Method in Class SMS_TaskSequence](savetoxml-method-in-class-sms_tasksequence) method, because it retains all passwords (secret information) and product keys (quasi-secret information). Used by itself, this method is not secure when used for saving XML to a file for use by another site.

Your application uses `ExportXml` to translate between task sequence WMI code and task sequence XML. It first calls the [SaveToXml Method in Class SMS_TaskSequence](savetoxml-method-in-class-sms_tasksequence) to create task sequence XML, preserving passwords and product keys. Then the application must call `ExportXml` and save the resulting information to a file, clearing all passwords (secret information) and product keys (quasi-secret information).

Remember that this method does not serialize task sequence XML for an [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class) object. For a package, you must reflect the task sequence XML by using the &lt;sequence&gt;&lt;/sequence&gt; tags.

## Requirements