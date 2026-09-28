---
layout: Conceptual
title: Validate Your App Protection Policy Setup - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/validate-policy-setup
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Learn how to test that your app protection policy is set up and working correctly in Microsoft Intune.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: 4c0d159c-b74d-31a5-6712-ca3ec9117193
document_version_independent_id: 4c0d159c-b74d-31a5-6712-ca3ec9117193
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/validate-policy-setup.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/validate-policy-setup
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/validate-policy-setup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 754e8198-dcd4-7051-2e97-89a44c4951dc
---

# Validate Your App Protection Policy Setup - Microsoft Intune | Microsoft Learn

Validate that your app protection policy is correctly set up and working. This guidance applies to app protection policies in the portal.

## Checking for symptoms

Users are unlikely to report issues since app protection is a data protection tool. If there's a problem with the app protection configuration, the user will have unrestricted access, as they would have without app protection, and they wouldn't know there's an issue. For this reason, we recommend you validate your app protection configuration by piloting your app protection policies with a small group of users who can deliberately test the app protection restrictions.

## What to check

If testing shows that your app protection policy behavior isn't functioning as expected, check these items:

- Are the users licensed for app protection?
- Are the users licensed for Microsoft 365?
- Is the status of each of the users' app protection apps as expected. The possible statuses for the apps are **Checked in** and **Not checked in**.

### User app protection status

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Monitor** &gt; **App protection status**, and then select the **Assigned users** tile.
3. On the **App reporting** page, select **Select user** to bring up a list of users and groups.
4. Search for and select a user from the list, then choose **Select user**. At the top of the **App reporting** pane, you can see whether the user is licensed for app protection. You can also see whether the user has a license for Microsoft 365 and the app status for all of the user's devices.

## What to do

Here are the actions to take based on the user status:

- If the user isn't licensed for app protection, assign an [Intune license](../../fundamentals/licensing) to the user.
- If the user isn't licensed for Microsoft 365, get a [license](../../fundamentals/licensing) for the user.
- If a user's app is listed as **Not checked in**, check if you've correctly configured an [app protection policy](validate-policy-setup) for that app.
- Ensure that these conditions apply across all users to which you want [app protection policies](monitor-policies) to apply.