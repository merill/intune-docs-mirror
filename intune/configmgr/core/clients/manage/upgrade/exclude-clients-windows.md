---
layout: Conceptual
title: Exclude client upgrades for Windows - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows
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
description: Learn how to exclude Windows clients from getting upgraded in Configuration Manager.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 2e94907a-abfd-7c8b-344a-eac47939cbfe
document_version_independent_id: f7bb4da7-e722-bb4b-d65d-81741a6a5996
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/upgrade/exclude-clients-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 386f5561-0ea5-704e-3616-f0bd6109d8d8
---

# Exclude client upgrades for Windows - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can exclude a collection of clients from automatically installing updated client versions. Use this exclusion for a collection of computers that need greater care when upgrading the client. A client that's in an excluded collection ignores requests to install updated client software.

This exclusion applies to the following methods:

- Automatic upgrade
- Software update-based upgrade
- Logon scripts
- Group policy

Note

Although the user interface states that clients won't upgrade via any method, there are two methods you can use to override these settings. Use client push or manual client installation to override this configuration. For more information, see How to upgrade an excluded client.

## Configure exclusion

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, select the **Sites** node, and then select **Hierarchy Settings** in the ribbon.
2. Switch to the **Client Upgrade** tab.
3. Select the option to **Exclude specified clients from upgrade**. Then select the **Exclusion collection** you want to exclude. You can only select a single collection for exclusion.
4. Select **OK** to close and save the configuration.

![Hierarchy settings window, client upgrade tab, highlighting exclusion settings.](media/automatic-upgrade-exclusion.png)

After clients in the excluded collection update policy, they don't automatically install client updates. For more information, see [How to upgrade clients for Windows computers](upgrade-clients-for-windows-computers).

Note

Excluded clients still download and run Ccmsetup, but don't upgrade.

When you remove a client from the exclude collection, it doesn't automatically upgrade until the next auto-upgrade cycle.

## How to upgrade an excluded client

If a device is a member of a collection that you excluded from upgrade, you can still upgrade the client using one of the following methods:

- **Client push installation**: Ccmsetup allows client push installation because it's your direct intent. This method lets you upgrade a client without removing it from the collection, or removing the entire collection from exclusion.
- **Manual client installation**: Manually upgrade an excluded client by using the following Ccmsetup command-line parameter: `/IgnoreSkipUpgrade`

    If you attempt to manually upgrade a client that's a member of the excluded collection, and don't use this parameter, the client doesn't upgrade. For more information, see [How to install Configuration Manager clients manually](../../deploy/deploy-clients-to-windows-computers#BKMK_Manual).