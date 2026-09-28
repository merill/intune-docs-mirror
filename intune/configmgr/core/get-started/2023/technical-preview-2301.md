---
layout: Conceptual
title: Technical preview 2301 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2301
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2301.
ms.date: 2023-01-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 217965fe-bfea-399c-794c-9fbbc6138ac9
document_version_independent_id: 217965fe-bfea-399c-794c-9fbbc6138ac9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2301.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2301
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2301.md
platformId: 6094cc4a-d0b4-cfd2-6fa8-a4c4438b89e1
---

# Technical preview 2301 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2301. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Microsoft Configuration Manager product branding

Starting with Configuration Manager version 2301 technical preview Microsoft Endpoint Configuration Manager is now Microsoft Configuration Manager

Microsoft Configuration Manager is an integrated solution for managing all your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. Continue to leverage your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

## Improvements to Cloud Sync (Collections to Microsoft Entra group Synchronization) feature

Starting this technical preview 2301 release user/device-based sync status (success, failure, in-progress, failure reason if any) will be available in the dashboard for the chosen collection. Earlier with Configuration Manager version 2211, the scalability of this feature has been improved with better throttling and error handling. Additionally, dedicated dashboards for user collections and device collections are added in Monitoring workspace to show Cloud Sync status. The dashboard displays the Cloud Sync status per collection with the mapped Microsoft Entra group, total member count, synced member count, status (success, failed, in progress) and last sync details.

User/device based sync status dashboard for chosen collection

[![Screenshot that displays the collection sync status.](media/14716797-aad-groups.png)](media/14716797-aad-groups.png#lightbox)

## Update to the default value of supersedence age in months for software updates

With Unified Update Platform (UUP) nearing general availability release, the feature update and non-feature update supersedence should be greater than 3. For new software update role installations we're updating this to 6, existing customer can review and update to 6 when the feature is released during general availability.

Update to the default value of supersedence age in months for software updates.

[![Screenshot of SUP properties. It displays the behavior of software updates supersedence.](media/16441147-uup-readiness.png)](media/16441147-uup-readiness.png#lightbox)

## Removing Microsoft Store for Business and Education new config capability

As part of Microsoft Store for Business deprecation, we are making these changes to the customer experience with using this feature:

- Removing a user's ability to create new Microsoft Store for Business in Configuration Manager.
- Display a warning message box when user triggers a sync from Microsoft Store for Business.
- Display a warning in the Create Application Wizard when user attempts to create a new app from Store license information.

## General known issues

Update to the default value of supersedence age in months for software updates.

Removing SUP role in Admin Console does not reset the supersedence age property in WMI. As a result, while reconfiguring the role, the previously configured value is shown in the configuration window. This property needs to be reset to default value on role removal.

## Other Updates

Offset for recurring monthly maintenance window schedules. Based upon your feedback, you can now offset monthly maintenance window schedules to better align deployments with the release of monthly security updates. For example, using a maximum offset of seven days after the second Tuesday of the month, sets the maintenance window for next Monday.