---
layout: Conceptual
title: Upgrade Windows 10 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-upgrade-win10
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
description: Upgrade devices to a supported version of Windows 10 or later, which is required for co-management.
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: 2dbbc8f8-ad8d-d099-dfa0-d4e576e807ec
document_version_independent_id: c2b9421e-bad3-ae31-7a19-b8074e4e07cc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-upgrade-win10.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-upgrade-win10
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-upgrade-win10.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7972d847-0217-b4c1-ab4f-c2b3fd1a7461
---

# Upgrade Windows 10 - Configuration Manager | Microsoft Learn

As you work towards onboarding your organization to co-management, getting current is a significant hurdle for some customers. Co-management requires a supported version of Windows 10 or later. Once you update Windows and configure auto-enrollment, your clients are automatically enrolled to co-management.

In the following video, senior program manager Rob York and product marketing manager Locky Ainley discuss and demo upgrading to Windows 10 for co-management:

## Why upgrade?

Among other platform advancements, Windows 10 and later supports auto-enrollment. This behavior makes a device automatically enroll to Intune when it joined Microsoft Entra ID.

For more information, see [Enable Windows automatic enrollment](../../device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment).

## How to do it

Here are some tips we've learned from helping thousands of customers get current quickly:

- Use phased deployments to roll out this upgrade to the right people at the right times. For more information, see [Create phased deployments](../osd/deploy-use/create-phased-deployment-for-task-sequence).
- Use pre-caching to reduce user wait times. For more information, see [Configure pre-cache content](../osd/deploy-use/configure-precache-content).
- Use the default in-place upgrade task sequence template. Then configure your steps for pre- and post-upgrade, and any failure actions. For more information, see [Recommended task sequence steps for post-processing](../osd/understand/in-place-upgrade-recommendations#post-processing).
- If your environment has a highly mobile workforce, Configuration Manager supports in-place upgrade over the cloud management gateway (CMG). This feature allows you to upgrade your Windows clients when they're internet-based. For more information on the CMG, see [Deploy Windows in-place upgrade via CMG](../osd/deploy-use/deploy-task-sequence-over-internet#deploy-windows-in-place-upgrade-via-cmg).
- Offer an opt-in to co-management for users who want to be early adopters. This approach accelerates initial adoption. By identifying these people in advance, you can make sure good coverage in the early days of a rollout. You also receive validation and feedback from users that are happy for change and interested in more frequent releases. Early adopter programs generate interest in the new technologies and grow in size over time.

## Case studies

Microsoft IT deployed Windows 10 to 96,000 distributed users at Microsoft. The deployment included both remote users and users on the corporate network. The deployment completed in nine weeks. For more information on their experience, see [Deploying Windows 10 at Microsoft as an in-place upgrade](https://www.microsoft.com/insidetrack/blog/preparing-your-organization-for-a-seamless-windows-10-deployment/).

A large European software manufacturer successfully uses an early adopter group. After initial testing and piloting groups, approximately 2,000 employees receive the first update, upgrades, and software. This group includes IT staff and opt-in volunteers. This level of engagement with their users gives them a greater level of confidence when testing, and more credibility when mass rollouts begin.

## Contact FastTrack

If you need assistance with your Windows upgrade at any point in the process, go to [Microsoft FastTrack](https://microsoft.com/fasttrack/), sign in, and request assistance.

For more information, see [Get help from FastTrack](quickstart-fasttrack).