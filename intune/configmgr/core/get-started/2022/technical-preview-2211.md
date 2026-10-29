---
layout: Conceptual
title: Technical preview 2211 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2211
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2211.
ms.date: 2022-11-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
locale: en-us
document_id: 4b865fad-aade-770b-c1f5-83042137c915
document_version_independent_id: 4b865fad-aade-770b-c1f5-83042137c915
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2211.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2211
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2211.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
platformId: d2d68eb5-9937-c3e7-7bf6-edb73b452608
---

# Technical preview 2211 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2211. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Authorization failure message in admin service now shown in Status message viewer

Audit messages about authorization failure have been introduced in admin service. You can now view request details and status messages. These messages are shown in “All Status Message” at “Status Message Queries” in “Monitoring” ribbon. Previously these failures were logged in log files.

With the new audit messages we intend to avoid inconvenience of log files rollback. Details about the user, resource access attempts and the number of attempts for all the authorized requests made by user in a day will now be available. We're also auditing read operations for HTTPS requests and for cloud-initiated operations. This helps admins to scope permission and roles of users while also determining if there are any malicious users.

For more information, see [Administration Service documentation](../../../develop/adminservice/overview).

## Network Access Account (NAA) account usage alert

Network Access Account (NAA) account usage alert

If your site is configured with NAA account, you'll see this new prerequisite warning added. To improve the security of distribution points configured with NAA account, review the existing accounts and their relevant permissions. If it has more than minimal required permission, then remove and add a minimal permission account. Don't configure any administrator level permission accounts on the NAA. If the site server is configured with HTTPS / EHTTP, we recommend removing NAA account, which is unused.

For more information, see the description of this [permissions-for-the-network-access-account](../../plan-design/hierarchy/accounts#permissions-for-the-network-access-account).

## Improvements to Cloud Sync (Collections to Microsoft Entra group Synchronization) feature

Starting with Configuration Manager version 2211, the scalability of this feature has been improved with better throttling and error handling. Additionally, dedicated dashboards for user collections and device collections are added in Monitoring workspace to show Cloud Sync status. The dashboard displays the Cloud Sync status per collection with the mapped Microsoft Entra group, total member count, synced member count, status (success, failed, in progress) and last sync details.