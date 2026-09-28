---
layout: Conceptual
title: Pre-release features - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/pre-release-features
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
description: Pre-release features are features that are in the current branch for early testing in a production environment.
ms.date: 2022-12-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 81a568fa-c391-5f8e-0fa7-dcac3d75333f
document_version_independent_id: d8e17e9d-c2fb-7fde-358d-0b11a0f802de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/pre-release-features.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/pre-release-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/pre-release-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96f6b0a2-2fd7-4de1-936d-89ad6e0eb7cc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ef8b0a5a-ba0a-4ec0-8636-48246ccd954f
platformId: 1afbec6b-fd37-bd51-85ef-58dccfaf7879
---

# Pre-release features - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Pre-release features are features that are in the current branch for early testing in a production environment. These features are fully supported, but still in active development. They might receive changes until they move out of the pre-release category.

## Give consent

Before using pre-release features, give consent to use pre-release features. Giving consent is a one-time action per hierarchy that you can't undo. Until you give consent, you can't enable new pre-release features included with updates. After you turn on a pre-release feature, you can't turn it off.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. In the ribbon, select **Hierarchy Settings**.
3. On the **General** tab of Hierarchy Settings Properties, enable the option to **Consent to use pre-release features**.

## Enable pre-release features

When you install an update that includes pre-release features, those features are visible in the Updates and Servicing Wizard with the regular features included in the update.

### If consent is given

In the Updates and Servicing Wizard, enable pre-release features. Select the pre-release features as you would any other feature.

Optionally, wait to enable pre-release features later from the **Features** node under **Updates and Servicing** in the **Administration** workspace. Select a feature, and then select **Turn on** in the ribbon. Until you give consent, this option isn't available for use.

### If you haven't given consent

In the Updates and Servicing Wizard, pre-release features are visible but you can't enable them. After the update is installed, these features are visible in the **Features** node. However, you can't enable them until you give consent.

Important

In a multi-site hierarchy, you can only enable optional or pre-release features from the central administration site. This behavior ensures there are no conflicts across the hierarchy. 

If you gave consent at a stand-alone primary site, and then expand the hierarchy by installing a new central administration site, you must give consent again at the central administration site.

When you enable a pre-release feature, the Configuration Manager hierarchy manager (HMAN) must process the change before that feature becomes available. Processing of the change is often immediate. Depending on the HMAN processing cycle, it can take up to 30 minutes to complete. After the change is processed, restart the console before using the feature.

## List of pre-release features

| Feature | Added as pre-release | Added as a full feature |
| --- | --- | --- |
| [Cloud management gateway with virtual machine scale set](../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets) | Version 2010 | Version 2107 |
| [Orchestration groups](../../../sum/deploy-use/orchestration-groups) | Version 2002 | Version 2111 |
| [Task sequence deployment type](../../../apps/get-started/creating-windows-applications#bkmk_tsdt) | Version 2002 | ![Not yet](media/red-x.png) |
| [Task sequence debugger](../../../osd/deploy-use/debug-task-sequence) | Version 1906 | Version 2203 |
| [Application groups](../../../apps/deploy-use/create-app-groups) | Version 1906 | Version 2111 |

Tip

For more information on non-pre-release features that you must enable first, see [Enable optional features from updates](optional-features).

For more information on features that are only available in the technical preview branch, see [Technical Preview](../../get-started/technical-preview).