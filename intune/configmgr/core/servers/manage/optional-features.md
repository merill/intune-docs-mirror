---
layout: Conceptual
title: Optional features - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/optional-features
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
description: Updates to Configuration Manager include optional features, which you have to enable before use.
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: fa6577c3-63fd-c0b6-cb8b-e3fb7fc3ece5
document_version_independent_id: 8288d766-a94a-3eff-7269-44a21f2f976b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/optional-features.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/optional-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/optional-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f9344ac6-a6db-2edf-bc8b-1e08a425ccbd
---

# Optional features - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When an update includes one or more optional features, you can enable those features in your hierarchy. Enable features when the update installs, or return to the console later to enable the optional features.

To view available features and their status, in the console go to the **Administration** workspace, expand **Updates and Servicing**, and select the **Features** node. To enable a feature, select it in the list, and then select **Turn on** in the ribbon.

Your user account requires permissions to view and enable optional features. For more information, see [Permissions for in-console updates](prepare-in-console-updates#permissions).

When a feature isn't optional, it's automatically available for use. It doesn't appear in the **Features** node.

Important

In a multi-site hierarchy, enable optional or pre-release features only from the central administration site (CAS). This behavior makes sure there are no conflicts across the hierarchy.

When you enable a new feature or pre-release feature, the Configuration Manager hierarchy manager (HMAN) must process the change before that feature becomes available. Processing of the change is often immediate. Depending on the HMAN processing cycle, it can take up to 30 minutes to complete. After the change is processed, restart the console before you can use the feature.

When new cloud-based features are available in the Microsoft Intune admin center, or other attached cloud services for your on-premises Configuration Manager installation, you can opt in to these new features in the Configuration Manager console.

## List of optional features

The following features are optional in the latest version of Configuration Manager:

- [Remove the central administration site](../deploy/install/remove-central-administration-site)
- [BitLocker management](../../../protect/plan-design/bitlocker-management)
- [Application groups](../../../apps/deploy-use/create-app-groups)

Tip

For more information on features that require consent to enable, see [pre-release features](pre-release-features).

For more information on features that are only available in the technical preview branch, see [Technical Preview](../../get-started/technical-preview).