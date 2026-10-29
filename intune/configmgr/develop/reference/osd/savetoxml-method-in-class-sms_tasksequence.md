---
layout: Conceptual
title: SaveToXml Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence
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
description: In Configuration Manager, the SaveToXml WMI class method serializes a task sequence from WMI objects to XML.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b9defe5a-95de-cc7a-e98d-4b88bc52271b
document_version_independent_id: cc8f9937-bc4f-ab83-fad9-2d944d69dd2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e15cf396-c7b7-8d75-3e53-545a282d26f5
---

# SaveToXml Method - Configuration Manager | Microsoft Learn

The `SaveToXml` Windows Management Instrumentation (WMI) class method, in Configuration Manager serializes a task sequence from WMI objects to XML.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
String SaveToXml(
      SMS_TaskSequence TaskSequence,
      SMS_TaskSequence_Reference References[],
      UInt32 Flags
);
```

#### Parameters

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: [in]

An [SMS_TaskSequence Server WMI Class](sms_tasksequence-server-wmi-class) object representing the task sequence to serialize.

`References` Data type: `SMS_TaskSequence_Reference` Array

Qualifiers: [out]

[SMS_TaskSequence_Reference Server WMI Class](sms_tasksequence_reference-server-wmi-class) objects representing any packages and programs referenced in the XML that are required by the task sequence. The provider uses these objects to check against the packages and programs that exist on the site.

`Flags` Data type: `UInt32`

Qualifiers: [out]

Flags identifying serialization details. The only flag currently supported is 0x00000001, sequence deploys an operating system image.

## Return Values

A `String` data type containing the XML representation of the task sequence.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Important

Your application must use secure techniques when calling this method, because it retains all passwords (secret information) and product keys (quasi-secret information). It is secure if the XML is being saved to the database through the task sequence package. This method is not secure, however, if the XML is being saved to a file for use by another site. In this case, the call must be followed by a call to the [ExportXml Method in Class SMS_TaskSequence](exportxml-method-in-class-sms_tasksequence) to strip out the passwords and product keys.

Your application uses this method when saving task sequences and translating between task sequence WMI code and task sequence XML, preserving passwords and product keys. The most common use is by an outside provider that is manipulating the WMI object model.

Remember that this method does not serialize task sequence XML for an [SMS_TaskSequencePackage Server WMI Class](sms_tasksequencepackage-server-wmi-class) object. For a package, you must reflect the task sequence XML using the &lt;sequence&gt;&lt;/sequence&gt; tags.

## Requirements