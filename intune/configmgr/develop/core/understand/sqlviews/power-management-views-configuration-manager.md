---
layout: Conceptual
title: Power management views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/power-management-views-configuration-manager
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
description: Information about the power plans applied to computers by Configuration Manager.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ff65614c-89f1-9200-1ab2-2335b06f13f6
document_version_independent_id: f4f73538-3af9-8635-2886-72d681ab6d8b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/power-management-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/power-management-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/power-management-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 31a8a090-8d1b-1bbd-0333-b85b898720a0
---

# Power management views - Configuration Manager | Microsoft Learn

Information about the power plans applied to computers by Configuration Manager and the power capabilities of computers is retrieved by Configuration Manager hardware inventory.

For more information about power management, see [Power management in Configuration Manager](../../../../core/clients/manage/power/introduction-to-power-management).

Wake-up proxy is used to supplement the traditional wake-up packet method by using the wake-up proxy client settings. Wake-up proxy uses a peer-to-peer protocol and elected computers to check whether other computers on the subnet are awake, and to wake them if necessary.

For more information about wake-up proxy, see the Power Management section of the [About client settings in Configuration Manager](../../../../core/clients/deploy/about-client-settings) topic in the Configuration Manager Documentation Library.

## Power management views

The power management views are described in this section.

### v\_GS\_POWER\_MANAGEMENT\_CAPABILITIES

Lists information about the power management capabilities collected from each client computer, sorted by resource ID, including information about the last time this information was collected, information about the battery, if present, and information about the wake up capabilities of the computer. The view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_MANAGEMENT\_CLIENTOPTOUT\_SETTINGS

Lists information for each client computer about whether the administrator allows the computer to opt out from power management settings and whether the client computer has been opted out from the settings. This view is sorted by resource ID.

### v\_GS\_POWER\_MANAGEMENT\_CONFIGURATION

Lists information about power plan names and the duration of each power plan that have been applied to client computers. The view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_MANAGEMENT\_DAY

Lists information about power activity on computers for each hour of the day. The view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_MANAGEMENT\_MONTH

List information about power activity on computers for the previous month, such as when the computer was active, when it was turned on, and when it was inn sleep mode. The view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_MANAGEMENT\_SETTINGS

Lists information about the power management settings applied to each computer, sorted by resource ID. These settings include the power plan applied to the computer, the delay before the screen and hard disks are turned off, and the action that will be taken when the computer power button is pressed. The view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_MANAGEMENT\_SUSPEND\_ERROR

Lists information, by Resource ID, about power management suspend operations that didn't complete successfully. The view can be joined to other views by using the **ResourceID** column.

## Wake up proxy views

The wake up proxy views are described in this section.

### v\_WakeupProxyDeploymentState

Lists information about the computers in each collection and whether that computer is enabled for wake-up proxy. This view is sorted by collection ID. This view can be joined to other views by using the **CollectionID** column.