---
layout: Conceptual
title: Upgrade the LTSB to current branch - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/convert-to-current-branch
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
description: Learn how to convert a long-term servicing branch (LTSB) site to a current branch site.
ms.date: 2017-02-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: 2f20797f-f36f-2508-14f0-068bbe0e47c8
document_version_independent_id: 1791e69c-9be3-8ae8-9a54-c09ce7576e91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/convert-to-current-branch.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/convert-to-current-branch
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/convert-to-current-branch.md
cmProducts: []
platformId: d772230e-6921-e856-d7b2-976749e1f0c7
---

# Upgrade the LTSB to current branch - Configuration Manager | Microsoft Learn

*Applies to: System Center Configuration Manager (Long-Term Servicing Branch)*

Use this topic to learn how to upgrade (convert) a site and hierarchy that runs the Long-Term Servicing Branch (LTSB) of Configuration Manager to the Current Branch.

When you have a current Software Assurance agreement (or similar licensing rights) that grants you rights to use the Current Branch, you can convert your installation from the LTSB to the Current Branch. This is a one-way conversion because there is no support for converting a Current Branch site to the LTSB.

If you have multiple sites, you only need to convert the top-tier site of your hierarchy. After the top-tier site is converted:

- Child primary sites automatically convert.
- You must manually update secondary sites from within the Configuration Manager console.

## Run setup to convert the Long-Term Servicing Branch

On the top-tier site of your hierarchy, you can run Configuration Manager setup from qualifying baseline media and select **Site maintenance**. Then, when presented with the licensing page, select the option for the Current Branch and complete the wizard.

When your site has converted to the Current Branch, previously unavailable features and capabilities will be available for use.

Note

Qualifying baseline media is a media that has a version that is equal to or later than your LTSB installation.

For example, because the LTSB is based on version 1606, you cannot use the baseline 1511 media to convert to the Current Branch. Instead, you run setup from the same version 1606 baseline media that you used to install the LTSB site, and choose the licensing option for the Current Branch. Alternately, if a later baseline of the Current Branch has been released, you can run setup from that baseline media.

For a list of baseline versions, see **Baseline and update versions** in [Updates for Configuration Manager](../servers/manage/updates).

## Use the Configuration Manager console to convert the long-term servicing branch

If your site runs the LTSB, you can use the following option in the Configuration Manager console to convert to the Current Branch:

1. In the console, go to **Administration** &gt; **Site Configuration** &gt; **Sites**, and then open **Hierarchy Settings**.
2. In **Hierarchy Settings**, switch to the **Licensing** tab. Select the option to **Convert to Current Branch**, and then choose **Apply**.

When your site has converted to the Current Branch, previously unavailable features and capabilities will be available for use.