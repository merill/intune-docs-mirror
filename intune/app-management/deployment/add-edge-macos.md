---
layout: Conceptual
title: Add Microsoft Edge to macOS Devices Using Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-edge-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- macOS
- FocusArea_Apps_Add
ms.reviewer: arnab
ms.subservice: apps
description: Learn about adding Microsoft Edge to macOS devices using Microsoft Intune.
ms.date: 2025-10-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9696d130-030c-0cc1-9b3e-6782b81a2341
document_version_independent_id: 9696d130-030c-0cc1-9b3e-6782b81a2341
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-edge-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-edge-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-edge-macos.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 33c73a1c-84e4-2ba2-5c0f-400a5ca8e6f5
---

# Add Microsoft Edge to macOS Devices Using Microsoft Intune - Microsoft Intune | Microsoft Learn

Before you can deploy, configure, monitor, or protect apps, you must add them to Intune. One of the available [app types](./#app-types-in-microsoft-intune) is Microsoft Edge *version 77 and later*. By selecting this app type in Intune, you can assign and install Microsoft Edge *version 77 and later* to devices you manage that run macOS. This app type makes it easy for you to assign Microsoft Edge to macOS devices without requiring you to use the macOS app wrapping tool. To help keep the apps more secure and up to date, the app comes with Microsoft AutoUpdate (MAU).

Important

This app type offers developer and beta channels for macOS. The deployment is in English (EN) only, however end users can change the display language in the browser under **Settings** &gt; **Languages**.

## Prerequisites

- The macOS device must be running macOS 10.14 or later before installing Microsoft Edge.

## Add Microsoft Edge to Intune

You can add Microsoft Edge version 77 and later to Intune using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **App type** list under the **Microsoft Edge, version 77 and later**, select **macOS**.

## Configure app information

In this step, you provide information about this app deployment. This information helps you identify the app in Intune, and it helps users find the app in the company portal.

1. Click **App information** to display the **App information** pane.
2. In the **App information**pane, you provide information about this app deployment. This information helps you identify the app in Intune, and it helps users find the app in the company portal.
    - **Name**: Enter the name of the app as it will be displayed in the company portal. Make sure that all names are unique. If the same app name exists twice, only one of the apps is displayed to users in the company portal.
    - **Description**: Enter a description for the app. For example, you could list the targeted users in the description.
    - **Publisher**: Microsoft appears as the publisher.
    - **Category**: Optionally, select one or more of the built-in app categories or a category that you created. This setting makes it easier for users to find the app when they browse the company portal.
    - **Display this as a featured app in the Company Portal**: Select this option to display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Microsoft appears as the developer.
    - **Owner**: Microsoft appears as the owner.
    - **Notes**: Optionally, enter any notes that you want to associate with this app.
3. Select **OK**.

## Configure Microsoft Edge settings

In this step, configure installation options for the app.

1. In the **Add App** pane, select **App settings**.
2. In the **App settings** pane, select either **Stable**, **Beta** or **Dev** from the **Channel** list to determine which Edge Channel you will deploy the app from. For more information, see [Microsoft Edge release schedule](/en-us/DeployEdge/microsoft-edge-release-schedule).

    - **Stable** channel is the recommended channel for deploying broadly in Enterprise environments. It updates every four weeks, each release incorporating improvements from the Beta channel.
    - **Beta** channel is the most stable Microsoft Edge preview experience and the best choice for a full pilot within your organization. With major updates every four weeks, each release incorporates the learnings and improvements from the Dev channel.
    - **Dev** channel is ready for enterprise feedback on Windows, Windows Server and macOS. It updates every week and contains the latest improvements and fixes.

    Note

    The Microsoft Edge browser logo is displayed with the app when users browse the company portal.
3. Select **OK**.

## Select scope tags (optional)

You can use scope tags to determine who can see client app information in Intune. For full details about scope tags, see Use role-based access control and scope tags for distributed IT.

1. Select **Scope (Tags)** &gt; **Add**.
2. Use the **Select** box to search for scope tags.
3. Select the check box next to the scope tags you want to assign to this app.
4. Click **Select** &gt; **OK**.

## Add the app

When you've completed configuring, select **Add** from the **App app** pane.

The app you've created is displayed in the apps list, where you can assign it to the groups that you select.