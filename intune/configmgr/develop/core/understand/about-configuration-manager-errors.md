---
layout: Conceptual
title: Configuration Manager Errors - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors
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
description: In Configuration Manager, when a Configuration Manager error occurs it's either a Windows Management Instrumentation (WMI) or an SMS Provider error.
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: d4dc907d-ccdc-8288-0709-e83c4c364da1
document_version_independent_id: fefd5be4-f4d8-ec58-1a75-f71dac0e925a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/about-configuration-manager-errors.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/about-configuration-manager-errors
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/about-configuration-manager-errors.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 7a9514a6-ec40-f9cb-c205-3389fb8b9bfd
---

# Configuration Manager Errors - Configuration Manager | Microsoft Learn

In Configuration Manager, when a Configuration Manager error occurs it's either a Windows Management Instrumentation (WMI) or an SMS Provider error.

A WMI error is reported in an instance of \_\_ExtendedStatus. An SMS Provider error is reported in an instance of `SMS_ExtendedStatus`.

How you process an error depends on the programming language that you're using.

## Error Handling with WMI

In VBScript the error object `Number` property is non-zero if an error occurs during synchronous operation. Typically, you check this value after making changes to, or querying, the SMS Provider. In an asynchronous operation you receive an error object of the `OnCompleted` callback function.

After you get the error object instance, you can check the \_\_Class property to determine the origin of the error. WMI creates an instance of \_\_ExtendedStatus for WMI errors, and the SMS Provider creates an instance of `SMS_ExtendedStatus` for SMS Provider errors. `SMS_ExtendedStatus` is derived from \_\_ExtendedStatus. The details of an SMS Provider error can also be found in SMSProv.log.

For more information about handling synchronous errors, see [How to Handle Configuration Manager Synchronous Errors by Using WMI](how-to-handle-configuration-manager-synchronous-errors-by-using-wmi).

For more information about handling asynchronous errors, see [How to Handle Configuration Manager Asynchronous Errors by Using WMI](how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi).

## Error Handling with the Managed SMS Provider

To handle Configuration Manager errors by using the managed SMS Provider, you catch the Configuration Manager-specific exceptions.

| Exception | Description |
| --- | --- |
| `SmsQueryException` | `SmsQueryException` is raised when a Configuration Manager query error occurs. It provides exception information specific to Configuration Manager (`SMS_ExtendedStatus`) and also encapsulates any WMI exceptions raised.`SmsQueryException.ErrorCode` maps to the equivalent System.ManagementException exception code.`SmsQueryException.ExtendStatusCode` maps to the SMS Provider error code raised in `SMS_ExtendedStatus.ErrorCode`. |
| `SmsConnectionException` | `SmsConnectionException` is raised when the connection to WMI is lost. |
| `SmsException` | `SmsException` is the base class from which `SmsQueryException` and `SmsConnectionException` derive. It's never raised but can be caught to catch both `SmsQueryException` and `SmsConnectionException`. |

### Accessing the \_\_ExtendedStatus and the SMS\_ExtendedStatus objects

Because the \_\_ExtendedStatus and `SMS_ExtendedStatus` aren't wrapped by the managed SMS Provider, you must use the System.Management ManagedException object.

If you don't need access to the error WMI objects, you can get access to an exception details string in SMSException.Details.

For more information about handling synchronous exceptions, see [How to Handle Configuration Manager Synchronous Errors by Using Managed Code](how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code).

For more information about handling asynchronous exceptions, see [How to Handle Configuration Manager Asynchronous Errors by Using Managed Code](how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code).