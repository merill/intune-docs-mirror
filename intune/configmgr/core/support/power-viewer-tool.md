---
layout: Conceptual
title: Power Viewer Tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/power-viewer-tool
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
description: Use the Power Viewer Tool to view the status of the power management feature on a Configuration Manager client.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ea102d2c-a712-2883-5bbf-ad463ccc1717
document_version_independent_id: 47ca9e75-d24d-be46-860b-1e7574b9264a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/power-viewer-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/power-viewer-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/power-viewer-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 8e020495-8301-3425-9944-e60d277cb65e
---

# Power Viewer Tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Power Viewer tool is one of the [Configuration Manager tools](tools). Use it to view the status of the power management feature on a Configuration Manager client.

Run **PowerVwr.exe** as an administrator. When the tool launches, it displays the power capabilities and power settings of the local computer on the **Power Config** tab.

To view the power management data of a remote computer:

1. Go to the **File** menu, and click **Connect**.
2. Enter the **Computer** name, and a **Username** and **Password**, if necessary.

There are three tabs in Power Viewer:

- **Power Config**: View the power capabilities and power settings of the targeted computer.
- **Daily Activity**: View the daily activity charts of the client, which includes the following information:

    - **Computer on**: The power status of the computer in one day. Sleep mode is considered as power off.
    - **Monitor on**: On or off status of monitor in one day.
    - **User Active**: User activity information in one day.
- **Power Events**: View all of the daily power events. The client summarizes these events at 12:00 AM. This summarization generates data for the daily activity chart.