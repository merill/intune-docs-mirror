---
layout: Conceptual
title: Upgrade evaluation installs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install
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
description: Learn how to upgrade an evaluation installation to a full installation of Configuration Manager.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3b79f957-c8ec-f8fa-78a9-853c80cc9780
document_version_independent_id: 4cd59dfd-b403-76de-192e-c887929c740e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 038916bc-21de-5c00-faec-d0c1e368f7e9
---

# Upgrade evaluation installs - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If you installed Configuration Manager as an evaluation version, after 360 days the Configuration Manager console becomes read-only. You then need to activate the product from the **Site Maintenance** page in Setup. At any time before or after the 360-day period, you can upgrade to a full installation.

Note

When you connect a Configuration Manager console to an evaluation installation of Configuration Manager, the window title bar displays the number of days that remain until it expires. The number of days in the window title doesn't automatically refresh. It only updates when you make a new connection to a site.

You can upgrade the following sites that run an evaluation installation:

- Central administration site (CAS)
- Primary site

Configuration Manager doesn't consider secondary sites as evaluation installations. So after you upgrade a primary parent site to a full installation, you don't need to modify a secondary site.

## Prerequisites

To upgrade an evaluation version to a licensed version, you need the following requirements:

- A valid product license key to use during the upgrade.
- **Administrator** rights on the site server.

## Process

1. On the site server, run **.\BIN\X64\Setup.exe** from the Configuration Manager installation folder. Use this copy of Setup because site maintenance options aren't available when you run Setup from source media.
2. On the **Before You Begin** page, select **Next**.
3. On the **Getting Started** page, select **Perform site maintenance or reset the Site**, and then select **Next**.
4. On the **Site Maintenance** page, select **Upgrade the evaluation edition to a licensed edition**. Then enter a valid product key, and select **Next**.
5. On the **Microsoft Software License Terms** page, read and accept the license terms, and then select **Next**.
6. On the **Configuration** page, select **Close** to complete the wizard.

Note

Until you reconnect the console to the site, the title bar might indicate that the site is still an evaluation version.