---
layout: Conceptual
title: Technical preview 1911 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1911
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1911.
ms.date: 2019-11-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 973a693f-8741-5f78-4311-4e456f91b420
document_version_independent_id: 9e914020-79e6-6697-0e0f-e11b78ab0a72
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1911.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1911
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1911.md
platformId: 2f052fd8-f6f4-40fe-a642-4f6173ceab96
---

# Technical preview 1911 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1911. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Microsoft Configuration Manager

Configuration Manager is now part of the Microsoft Intune family of products.

![Microsoft Configuration Manager](media/4960084-endpoint-manager-logo.png)

Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. Continue to leverage your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

The following Microsoft management solutions are all now part of the **Microsoft Intune** brand:

- [Configuration Manager](/en-us/configmgr)
- [Intune](/en-us/mem/fundamentals/account-sign-up)
- [Desktop Analytics](../../../../device-updates/windows/monitor-compatibility)
- [Windows Autopilot](/en-us/autopilot/enrollment-autopilot)
- Other features in the [Device Management Admin Console](https://techcommunity.microsoft.com/t5/enterprise-mobility-security/microsoft-intune-rolls-out-an-improved-streamlined-endpoint/ba-p/937760)

For more information, see the following posts from Brad Anderson, Microsoft corporate vice president for Microsoft 365:

- [Announcement blog post](https://aka.ms/cmannounce)
- [Vision paper](https://aka.ms/MEMVisionPaper)
- [Announcement summary video](https://youtu.be/GS7oNPInFuw)

## Microsoft Connected Cache support for Intune Win32 apps

When you enable Microsoft Connected Cache on your Configuration Manager distribution points, they can now serve Microsoft Intune Win32 apps to co-managed clients.

Note

Configuration Manager current branch version 1906 included [Delivery Optimization In-Network Cache](../../plan-design/hierarchy/microsoft-connected-cache), an application installed on Windows Server that's still in development. Starting in technical preview branch version 1911 this feature is now called **Microsoft Connected Cache**.

When you install Connected Cache on a Configuration Manager distribution point, it offloads Delivery Optimization service traffic to local sources. Connected Cache does this behavior by efficiently caching content at the byte range level.

### Prerequisites

#### Client

- Update the client to the latest version.
- The client device needs to have at least 4 GB of memory.

    Tip

    Use the following group policy setting: Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Delivery Optimization &gt; **Minimum RAM capacity (inclusive) required to enable use of Peer Caching (in GB)**.

#### Site

- Enable Connected Cache on a distribution point. For more information, see [Delivery Optimization In-Network Cache](../../plan-design/hierarchy/microsoft-connected-cache).
- The client and the Connected Cache-enabled distribution point need to be in the same boundary group.
- Enable the following client settings in the [**Delivery Optimization**](../../clients/deploy/about-client-settings#delivery-optimization) group:

    - **Use Configuration Manager Boundary Groups for Delivery Optimization Group ID**
    - **Enable devices managed by Configuration Manger to use Microsoft Connected Cache servers for content download**
- Enable the pre-release feature **Client apps for co-managed devices**. For more information, see [Pre-release features](../../servers/manage/pre-release-features).
- Enable co-management, and switch the **Client apps** workload to **Pilot Intune** or **Intune**. For more information, see the following articles:

    - [Workloads - Client apps](../../../comanage/workloads#client-apps)
    - [How to enable co-management](../../../comanage/how-to-enable)
    - [Switch workloads to Intune](../../../comanage/how-to-switch-workloads)

        If in pilot, add the client to the pilot collection for Client Apps.

#### Intune

- This feature only supports the Intune Win32 app type.

    - Create and assign (deploy) a new app in Intune for this purpose. (Apps created before Intune version 1811 don't work.) For more information, see [Intune Win32 app management](../../../../app-management/deployment/win32).
    - The app needs to be at least 100 MB in size.

        Tip

        Use the following group policy setting: Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Delivery Optimization &gt; **Minimum Peer Caching Content File Size (in MB)**.