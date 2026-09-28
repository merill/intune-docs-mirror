---
layout: Conceptual
title: Windows App Deployment by Using Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/deploy-windows
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
- FocusArea_Apps_Deploy
ms.reviewer: priyar
ms.subservice: apps
description: Learn about Windows app deployment scenarios available with Microsoft Intune.
ms.date: 2025-10-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7691b0f1-3d33-ccbb-8ff9-3f5ba3030a6a
document_version_independent_id: 7691b0f1-3d33-ccbb-8ff9-3f5ba3030a6a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/deploy-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/deploy-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/deploy-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/cd440f3c-1b78-40a7-97ba-aa00a1d79df7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c828f7e0-89b4-459c-9bae-d7ab1c4bd9ad
platformId: 10821c42-67d7-02f7-bba5-b2061b9ec184
---

# Windows App Deployment by Using Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune supports a variety of app types and deployment scenarios on Windows devices. After you've added an app to Intune, you can assign the app to users and devices. This article provides more details on the supported Windows scenarios, and also covers key details to note when you're deploying apps to Windows. For information about deploying an app, also known as assigning an app, see [Assign an app](assign-groups#assign-an-app) to a group.

A Line-of-business (LOB) app is the app type supported on Windows devices. The file extensions for Windows apps include .msi, .appx, and .appxbundle.

Note

To deploy modern apps, you need to use [supported Windows versions](../../fundamentals/ref-supported-platforms).

LOB app deployment isn't supported on devices running Windows Home editions.

## Supported Windows app types

Specific app types are supported based on the version of Windows that your users are running. The following table provides the app type and Windows supportability.

| App type | Home | Pro | Business | Enterprise | Education | S-Mode | HoloLens^1^ | Surface Hub |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| .MSI | No | Yes | Yes | Yes | Yes | No | No | No |
| .IntuneWin | No | Yes | Yes | Yes | Yes | 19H2+ | No | No |
| Office C2R | No | Yes | Yes | Yes | Yes | RS4+ | No | No |
| LOB: APPX/MSIX | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [Microsoft Store app (new)](add-microsoft-store) | No | Yes | Yes | Yes | Yes | Yes | No | No |
| Web Apps | Yes | Yes | Yes | Yes | Yes | Yes | Yes^2^ | Yes^2^ |
| Store Link | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| Microsoft Edge | No | Yes | Yes | Yes | Yes | 19H2+^3^ | No | No |

^1^ To unlock app management, upgrade your HoloLens device to [Holographic for Business](../../solutions/windows-holographic).^2^ Launch from the Company Portal only.^3^ For Edge app to install successfully, devices must also be assigned an S-Mode policy.

Note

All Windows app types require enrollment.

## Windows LOB apps

You can upload Windows LOB apps to the Microsoft Intune admin center. These can include modern apps, such as Universal Windows Platform (UWP) apps and Windows App Packages (AppX), as well as Win 32 apps, such as simple Microsoft Installer package files (MSI). The admin must manually upload and deploy updates of LOB apps. These updates are automatically installed on user devices that have installed the app. No user intervention is required, and the user has no control over the updates.

## Install apps on Windows devices

Depending on the app type, you can install the app on a Windows device in one of two ways:

- **User Context**: When an app is deployed in user context, the managed app is installed for that user on the device when the user signs in to the device. Note that the app installation doesn't succeed until the user signs in to the device.
    - Modern LOB apps and Microsoft Store apps can be deployed in user context. The apps support both the Required and Available intents.
    - Win32 apps built as User Mode or Dual Mode can be deployed in user context, and support both the Required and Available intents.
- **Device Context**: When an app is deployed in device context, the managed app is installed directly to the device by Intune.
    - Modern LOB can be deployed in device context. These apps only support the Required intent.
    - Win32 apps built as Machine Mode or Dual Mode and Microsoft Store apps can be deployed in device context, and support both the Required and Available intents.

Note

For Win32 apps built as Dual Mode apps, the admin must choose if the app will install as a User Mode or Machine Mode app for all assignments associated with that instance. The deployment context can't be changed per assignment.

Apps can only be installed in the device context when supported by the device and the Intune app type. Device context installs are supported on Windows desktops and Teams devices, such as the Surface Hub. They aren't supported on devices running Windows Holographic for Business, such as the Microsoft HoloLens.

You can install the following app types in the device context and assign these apps to either a device or user group:

- Win32 apps
- LOB apps (MSI, APPX and MSIX)
- Microsoft 365 Apps for enterprise
- Microsoft Store apps

Windows LOB apps (specifically APPX and MSIX) that you've selected to install in device context must be assigned to a device group. The installation fails if one of these apps is deployed in the user context. The following status and error appears in the admin center:

- Status: Failed.
- Error: A user can't be targeted with a device context install.

Important

When used in combination with a Windows Autopilot pre-provisioning scenario, there is no requirement for LOB apps deployed in device context to target a device group. For more information, see [Windows Autopilot pre-provisioning deployment](/en-us/autopilot/pre-provision).

Note

After you save an app assignment with a specific deployment, you can't change the context for that assignment, except for modern apps. For modern apps, you can change the context from user context to device context.

If there's a conflict in policies on a single user or device, the following priorities apply:

- A device context policy is a higher priority than a user context policy.
- An install policy is a higher priority than an uninstall policy.

For more information, see [Include and exclude app assignments in Microsoft Intune](configure-assignment-scope). For more information about app types in Intune, see [Add apps to Microsoft Intune](./).