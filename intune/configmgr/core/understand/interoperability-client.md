---
layout: Conceptual
title: Extended interoperability client - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/interoperability-client
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
description: Learn about using the extended interoperability client for long-term support of a static Configuration Manager client with a current branch site.
ms.date: 2021-06-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0a6e24f9-3014-8d9f-7ff4-82ba9db28a41
document_version_independent_id: e1a59107-1a25-01ca-9507-b42d20da7401
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/interoperability-client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/interoperability-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/interoperability-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6defd789-9003-d835-57d3-e958993935c0
---

# Extended interoperability client - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Business requirements might not allow you to regularly update the Configuration Manager client on some devices. For example, you need to follow change management policies, or the device is mission-critical. Accommodate these needs by installing a new client for long-term use, called the extended interoperability client (EIC). Only use the EIC for specific devices that can't be frequently updated, like kiosk or point-of-sale devices. Continue to use [automatic client upgrade](../clients/manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate) for most of your clients.

## How it works

Typically, when you install a new [in-console update](../servers/manage/install-in-console-updates) for Configuration Manager, clients automatically update their client software so they can use those new features. With this scenario, you still update to the current branch receiving the new features and updates. Most devices update the Configuration Manager client software with each version update you install. However, on a subset of critical systems that you don't want to receive client software updates, you install the extended interoperability client. These clients don't install new client software until you explicitly deploy a new version of the client software to them.

## Supported versions

For more information on the current supported versions, see [Support for Configuration Manager current branch versions](../servers/manage/updates#supported-versions).

Tip

The EIC is supported for the client versions which are still in the supported list of Configuration Manager versions. For example, when Configuration Manager 2503 is the latest CB version, EIC supported client version can be on 2403.

Plan to update the extended interoperability client on devices that you manage with the current branch before support for the client expires. To do so, download a new version of the client from Microsoft, and then deploy that updated client software to your devices that use the current extended interoperability client.

## How to use the EIC

1. Add these devices to a collection, and exclude that collection from automatic client upgrades. For more information, see [How to exclude clients from upgrade](../clients/manage/upgrade/exclude-clients-windows).
2. Obtain a supported version of the EIC from the `\SMSSETUP\Client` folder of the Configuration Manager update installation media. Make sure that you copy the entire contents of the folder.
3. Manually install the EIC on those devices. For more information, see [Manually install the client](../clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

## Limitations

- Updates for the extended interoperability client software aren't available by using in-console updates. For more information on how to update the EIC, see [How to upgrade an excluded client](../clients/manage/upgrade/exclude-clients-windows#how-to-upgrade-an-excluded-client).
- The EIC only supports the following features:

    - Software updates
    - Hardware and software inventory
    - Packages and programs