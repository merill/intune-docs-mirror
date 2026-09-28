---
layout: Conceptual
title: Service Windows - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/service-windows
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
description: Use service windows to control when Configuration Manager sites install updates.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 3d2ec3f2-26e8-d8e3-32f8-02a07e15735c
document_version_independent_id: 885f915c-83a7-bbf8-c741-8e796b878302
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/service-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/service-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/service-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3e855261-9d1d-c93e-da24-df60bf7454aa
---

# Service Windows - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To control when in-console updates can install, configure service windows. You can add service windows at the central administration site (CAS) and primary sites. Each site can have multiple service windows. The site determines when it can install an update by the combination of all service windows that it has.

Tip

A *service window* is for a site server. A *maintenance window* is for a client. For more information, see [How to use maintenance windows](../../clients/manage/collections/use-maintenance-windows).

## Default behavior

When you don't configure a service window:

- On your top-tier site, you choose when to start the update installation. The top-tier site is either the CAS or a stand-alone primary site.
- On a child primary site, the update automatically installs after it successfully completes at the CAS.
- On a secondary site, updates never start automatically. After the parent primary site updates, manually start the update from the console.

## Behavior with a service window

When you create one or more service windows:

- On your top-tier site, you can't start the installation of any new update from the console until the time is in the service window. Even with a service window, the site still automatically downloads updates so they're ready to install.
- On a child primary site, an update from the CAS downloads to the primary site, but doesn't automatically start. You can't manually start the install of an update outside of a service window. When service windows no longer block update installation, the primary site automatically starts the update installation.
- Secondary sites don't support service windows, and don't automatically install updates. After the parent primary site updates, manually start the update from the console.

## Configure a service window

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. Select the site server where you want to configure a service window.
3. In the ribbon, select **Properties**.
4. Switch to the **Service Windows** tab.
5. To add a new service window, select the new button (gold asterisk).
6. In the **Schedule** window, specify a name to describe the service window. This name helps you identify the service window in the console.
7. Configure the date, time, and recurrence pattern as necessary for this site.

    ![Example service window configuration](media/service-window.png)

After you create a service window, use the edit and delete buttons to make changes.