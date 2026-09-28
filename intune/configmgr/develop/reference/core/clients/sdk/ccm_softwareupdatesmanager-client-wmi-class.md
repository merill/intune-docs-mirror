---
layout: Conceptual
title: CCM_SoftwareUpdatesManager Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class
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
description: The CCM_SoftwareUpdatesManager WMI class is a client class that exposes methods to install, schedule and other actions on set of software updates.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 38283da2-0066-fc5d-23fc-6787becee1d1
document_version_independent_id: 66176f3c-81a0-def0-8cc9-0337a1e9b37b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class.md
cmProducts: []
platformId: e851f3ce-3420-ef5d-5766-29e8e9b302a8
---

# CCM_SoftwareUpdatesManager Class - Configuration Manager | Microsoft Learn

The `CCM_SoftwareUpdatesManager` WMI class is a client class, in Configuration Manager, that exposes methods to install, schedule and other actions on set of software updates.

This interface is equivalent to the ICCMUpdatesDeployment COM interface in the Configuration Manager 2007 SDK.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_SoftwareUpdatesManager();
```

## Methods

The following table shows the methods in the `CCM_SoftwareUpdatesManager` class.

| Method | Description |
| --- | --- |
| [CancelDownload Method in Class CCM_SoftwareUpdatesManager](canceldownload-method-in-class-ccm_softwareupdatesmanager) | Cancels an in-progress download of software updates during a deployment. |
| [GetAllUpdatesUserExperience Method in Class CCM_SoftwareUpdatesManager](getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager) | Gets the user experience mode that determines how software updates are displayed on a target computer. |
| [InstallUpdates Method in Class CCM_SoftwareUpdatesManager](installupdates-method-in-class-ccm_softwareupdatesmanager) | Installs the software updates. |
| [PostponeUpdatesToNonBusinessHours Method in Class CCM_SoftwareUpdatesManager](postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager) | Postpones a set of software updates to automatically install in non-business hours, which are specified by the user. |
| [SetAllUpdatesUserExperience Method in Class CCM_SoftwareUpdatesManager](setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager) | Sets the user experience mode that determines how software updates are displayed on a target computer. |

## Properties

The `CCM_SoftwareUpdatesManager` class does not define any properties.

## Remarks

This class is equivalent to the `ICCMUpdatesDeployment` class in Configuration Manager 2007 COM SDK.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).