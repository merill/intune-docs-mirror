---
layout: Conceptual
title: Technical preview 2411 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2024/technical-preview-2411
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2411.
ms.date: 2024-11-28T00:00:00.0000000Z
ms.topic: whats-new
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: tier3
locale: en-us
document_id: 2a00f1dd-a3fd-e59a-91c9-e42ab31c0a9c
document_version_independent_id: 2a00f1dd-a3fd-e59a-91c9-e42ab31c0a9c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2024/technical-preview-2411.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2024/technical-preview-2411
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2024/technical-preview-2411.md
platformId: 0b339ec3-271b-5d61-54c4-83d7bcac640b
---

# Technical preview 2411 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2411. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Operating System support added for Windows 11 24H2 and Windows Server 2025

With this version of Configuration Manager, support is added for Windows 11 24H2 and Windows Server 2025.

- Windows 11 24H2 & Windows Server 2025 are added to the product lifecycle dashboard and supported platform.
- Windows 11 24H2 & Windows Server 2025 client support is added.
- Boot image creation in CM on Windows Server 2025 now supports latest Windows ADK.
- Windows upgrade readiness dashboard now supports Windows 11 24H2 for upgrading clients.

Note

Windows Server and Windows 11 24H2 do not support Firewall rules. This will result in a non-compliant status in the Configuration Manager applet.

## Enhanced Security for CMG

CMG Setup now uses managed identities and third party **Server App** to interact with CMG's Azure storage account, instead of storage account keys.

- Hence storage account key access is disabled for new CMG setup.
- For sessions upgrading from earlier versions to 2411 tp, the **CMG Enhance Security** button is shown as enabled.

    [![Screenshot of cm enhanced window in the console.](media/27297018-cmg-enhanced.png)](media/27297018-cmg-enhanced.png#lightbox)
- When the enhanced security option is selected, the VMSS OS Auto Upgrade feature is also activated. An extra panel appears, prompting the admin to provide maintenance window details. Azure uses this information to schedule upgrades whenever new OS images become available.

    [![Screenshot of service window in the console.](media/27297018-service-window.png)](media/27297018-service-window.png#lightbox)

### CMG Entra Application secret key renewal

The 'Renew Secret Key' feature now opens a dialog with four options for the validity period. This update also prevents applications older than 800 days (approximately two years) from renewing their secret keys. The same options are available when creating a new app.

[![Screenshot of service window in the console.](media/27297018-secret-window.png)](media/27297018-secret-window.png#lightbox)

Sign in using tenant Global Administrator credentials and then click on the renew button.

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../understand/fundamentals-of-role-based-administration).

## SQL 2012 and 2014 support are deprecated

Starting with this version, Configuration Manager no longer supports SQL Server 2012 and 2014. Upgrade to the latest SQL Server version or at least SQL Server 2016. If you don’t upgrade, CM upgrades are blocked, and you see an error during the prereq check.

## Software metering support in Arm64 devices

The Configuration Manager now supports Software metering for Arm64 devices. Software metering is used to monitor Windows PC desktop apps with a filename ending in .exe. For more information, see [Software metering in Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering).