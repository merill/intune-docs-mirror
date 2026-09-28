---
layout: Conceptual
title: Add Microsoft Edge for Windows to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-edge-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Windows
ms.reviewer: arnab
ms.subservice: apps
description: Learn about adding Microsoft Edge for Windows to Microsoft Intune.
ms.date: 2025-10-02T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 
locale: en-us
document_id: dca372dd-e827-cf3e-64dc-da1ad2ddb8c3
document_version_independent_id: dca372dd-e827-cf3e-64dc-da1ad2ddb8c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-edge-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-edge-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-edge-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 8fce5142-3678-313e-eb54-5499d3395a78
---

# Add Microsoft Edge for Windows to Microsoft Intune - Microsoft Intune | Microsoft Learn

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Before you can deploy, configure, monitor, or protect apps, you must add them to Intune. One of the available [app types](./#app-types-in-microsoft-intune) is Microsoft Edge *version 77 and later*. By selecting this app type in Intune, you can assign and install Microsoft Edge *version 77 and later* to devices you manage that run Windows.

Important

This app type offers stable, beta, and dev channels for Windows. The deployment is in English (EN) only, however end users can change the display language in the browser under **Settings** &gt; **Languages**. Microsoft Edge is a Win32 app installed in system context and on like architectures (x86 app on x86 OS, and x64 app on x64 OS). Intune will detect any preexisting Microsoft Edge installations. If it is installed in user context, a system installation will overwrite it. If it is installed in system context, installation success is reported. In addition, automatic updates of Microsoft Edge are **On** by default.

You cannot use the built-in application deployment of Microsoft Edge for workplace join computers. Built-in application deployment requires the Intune management extension, which only exists for Microsoft Entra joined devices. You can still deploy Microsoft Edge *version 77 and later* using an *.msi* uploaded to **Apps**, see [Add a Windows line-of-business app to Microsoft Intune](add-lob-windows).

## Prerequisites

- A [supported Windows version](../../fundamentals/ref-supported-platforms)
- Any pre-installed versions of Microsoft Edge *version 77 and later* for all channels in user context will be overwritten with Edge installed in system context.

## Configure the app in Intune

You can add a Microsoft Edge version 77 and later to Intune using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **App type** list under the **Microsoft Edge, version 77 and later**, select **Windows 10**.

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

## Configure app settings

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

When you've completed configuring the app, select **Add** from the **App app** pane.

The app you've created is displayed in the apps list, where you can assign it to the groups that you select.

Note

Currently, if you unassign the deployment of Microsoft Edge, it will remain on the device.

## Uninstall the app

When you need to uninstall Microsoft Edge from user's devices, use the following steps.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; *Microsoft Edge* app &gt; **Assignments** &gt; **Add group**.
3. In the **Add group** pane, select **Uninstall**.

    Note

    The app is uninstalled from devices in the selected groups if Intune has previously installed the application onto the device via an **Available for enrolled devices** or **Required** assignment using the same deployment.
4. Select **Included Groups** to select the groups of users that are affected by this app assignment.
5. Select the groups that you want to apply the uninstall assignment.
6. Click **Select** on the **Select groups** pane.
7. Click **OK** on the **Assign** pane to set the assignment.
8. If you want to exclude any groups of users from being affected by this app assignment, select **Exclude Groups**.
9. If you have chosen to exclude any groups, in **Select groups**, select **Select**.
10. Select **OK** in the **Add group** pane.
11. Select **Save** in the app **Assignments** pane.

Important

To uninstall the app successfully, make sure to remove the members or group assignment for install before assigning them to be uninstalled. If a group is assigned to both install an app and uninstall an app, the app will remain and not be removed.

## Troubleshooting

**Microsoft Edge version 77 and later for Windows:** Intune uses the Intune management extension to download and deploy the Microsoft Edge installer to assigned Windows devices, then communicates the deployment settings to the Microsoft Edge installer, which downloads and installs the Microsoft Edge browser directly from the CDN. Reference the [prerequisites for the Intune management extension](../../device-management/tools/management-extension-windows#prerequisites), and the best practices outlined in accessing Azure Update Service and the CDN to ensure that your network configuration permits Windows devices to access these locations. In addition, to allow access to installation files from a CDN to install the browser, you need to allow access to Windows Update endpoints. For more information, see [Manage connection endpoints for Windows 10, version 1809 – Windows Update](/en-us/windows/privacy/manage-windows-1809-endpoints#windows-update) and [Network endpoints for Microsoft Intune](../../fundamentals/endpoints).