---
layout: FAQ
title: In-console updates FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates-faq
summary: ''
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
description: Frequently asked questions for Configuration Manager in-console updates.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: faq
locale: en-us
document_id: 5a4bbcf6-fe00-ab4a-ad34-c7f242e774a7
document_version_independent_id: 5c594d5e-35bc-8e32-4f6f-dcc384c08219
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/updates-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/updates-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/updates-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: c4c11afd-8a22-0d93-62ec-73cc760d8bc2
---

# In-console updates FAQ - Configuration Manager | Microsoft Learn

## Why don't I see certain updates in my console?

If you can't find a specific update in your console after a successful sync with the Microsoft cloud service, this behavior might be because of one of the following reasons:

- The update requires a configuration that your infrastructure doesn't use, or your current product version doesn't fulfill a prerequisite for receiving the update.

    If you think you have the required configurations and prerequisites for a missing update, confirm the service connection point is in online mode. Then, use the **Check for Updates** option in the **Updates and Servicing** node to force a check. If your service connection point is in offline mode, use the service connection tool to manually sync with the cloud service.
- Your account lacks the correct role-based administration permissions to view updates in the Configuration Manager console. For more information, see [Permissions to manage updates](prepare-in-console-updates#permissions).

## Why did the current branch name change with version 2103?

To better align with other releases within Microsoft Endpoint Manager, starting in the year 2021 the current branch version names will be 2103, 2107, and 2111. They will still release every four months, and release at the same time of the year.