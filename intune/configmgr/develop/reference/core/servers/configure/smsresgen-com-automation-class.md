---
layout: Conceptual
title: SMSResGen COM Automation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class
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
description: Use the SMSResGen COM class to automate the creation of a data discovery record (DDR).
ms.date: 2018-04-12T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1d874641-4cfb-74f3-3a32-590a1593eaab
document_version_independent_id: 6ee0a0d2-d9e3-2ca8-cc4f-7e984b730e6d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 9b82eaa5-8fc6-4388-a5d1-837c324cee2c
---

# SMSResGen COM Automation Class - Configuration Manager | Microsoft Learn

The `SMSResGen` COM class in Configuration Manager is used to create data discovery records (DDRs).

## Methods

| Name | Description |
| --- | --- |
| [ISMSResGen Interface](ismsresgen-interface) | Defines the data discovery record methods. |

## Remarks

`SMSResGen` is found in SMSResGenCtl.dll. Use the [ISMSResGen Interface](ismsresgen-interface) interface to create and use DDRs.

Important

The latest version of SMSRsGenCtl.dll is available from NuGet:

- [Microsoft.ConfigurationManagement.SMSRsGenCtl.i386](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGenCtl.i386/)
- [Microsoft.ConfigurationManagement.SMSRsGenCtl.amd64](https://www.nuget.org/packages/Microsoft.ConfigurationManagement.SMSRsGenCtl.amd64/)

Because the `SMSResGen` control is not thread safe, do not try to create more than one instance of this class.

Important

The function `DDRSendToSMS`, available in previous releases of the SDK and in versions of `SMSRsGen.dll`/`SMSResGenCtl.dll`, has been deprecated and should not be used with Configuration Manager.

The CLSID for `SMSResGen` is 19352BAD-BEE0-4193-95C4-588B6C5DBCD1.

## Requirements

### Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).