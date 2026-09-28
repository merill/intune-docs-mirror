---
layout: Conceptual
title: SMSEvent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class
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
description: The SmsEvent class represents a Configuration Manager event on the client. The class implements the ICcmEvent interface.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 888c02e8-233c-d3e2-a384-978cd03210a9
document_version_independent_id: 578344f2-97ae-5c4d-1dc9-857e1518673e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/smsevent-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/smsevent-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/smsevent-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: a7a3bca6-ef74-7886-2421-c7866a6779e8
---

# SMSEvent Class - Configuration Manager | Microsoft Learn

The `SmsEvent` class represents a Configuration Manager event on the client. The class implements the `ICcmEvent` interface.

## Methods and Properties

| Term | Description |
| --- | --- |
| [ICcmEvent::EventType Property](iccmevent--eventtype-property) | Indicates the type of Windows Management Instrumentation (WMI) event that is being raised. |
| [ICcmEvent::RawEvent Property](iccmevent--rawevent-property) | Adds information to custom events. |
| [ICcmEvent::SetProperty Method](iccmevent--setproperty-method) | Sets an event property. |
| [ICcmEvent::Submit Method](iccmevent--submit-method) | Submits an event to WMI. |
| [ICcmEvent::SubmitPending Method](iccmevent--submitpending-method) | Submits an event to WMI in situations where the Configuration Manager Agent Host (CCMEXEC) service might not be running. |

## Remarks

The `ProgID` for the automation object is Microsoft.SMS.Event and it is implemented as part of Smscore.dll. The Visual Basic reference for early binding is SMSCorLib. The early binding object name is `SMSEvent`.

## Requirements

smscore.dll

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).