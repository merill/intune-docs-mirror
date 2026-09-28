---
layout: Conceptual
title: Surface Hub Windows 10 Team device restrictions in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-surface-hub
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Add or configure Surface Hub devices settings running Windows 10 Team. Add a wake-up screen, create a maintenance window, use Miracast, and more in Microsoft Intune.
ms.date: 2025-10-14T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mikedano
ROBOTS: NOINDEX, NOFOLLOW
locale: en-us
document_id: 8c1ad43d-8223-11f6-c682-1abd0e206d52
document_version_independent_id: 8c1ad43d-8223-11f6-c682-1abd0e206d52
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-device-restrictions-surface-hub.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-device-restrictions-surface-hub
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-device-restrictions-surface-hub.md
platformId: e80faa8f-77a0-836a-0375-9219ee6b7041
---

# Surface Hub Windows 10 Team device restrictions in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

This article describes some of the Microsoft Intune device restrictions settings that you can configure for Surface Hub devices running [Windows 10 Team](/en-us/surface-hub/differences-between-surface-hub-and-windows-10-enterprise).

## Before you begin

- Create a [Windows 10 Teams device restrictions configuration profile](configure-device-restrictions#create-the-profile).
- Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

## Apps and experience

These settings use the [SurfaceHub CSP](/en-us/windows/client-management/mdm/surfacehub-csp).

- **Wake screen when someone in room**: **Block** prevents the screen from waking automatically when its sensor detects someone in the room. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Meeting information displayed on welcome screen**: Select the information that shows on the Meetings tile of the Welcome screen. Your options:
    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Organizer and time only**: Shows the organizer and time of the meeting.
    - **Organizer, time, and subject (subject hidden for private meetings)**: Shows the organizer, time, and subject of the meeting. The subject is hidden for private meetings.
- **Welcome screen background image URL**: Enter the URL of a `.png` image. On the Windows devices, this image shows as the background during user sessions, and on the **Welcome** screen. The image must be in PNG format, and the URL must begin with `https://`.
- **Auto-launch Connect**: **Block** prevents the Connect app from automatically opening when a projection is started. If blocked, users can manually launch the Connect app from the Hub's settings. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Sign-in suggestions**: **Block** disables autofilling the sign-in dialog with invitees from scheduled meetings. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **My meetings and files**: **Block** disables the **My meetings and files** feature in the Start menu. This feature shows the signed-in user's meetings and files from Microsoft 365. When set to **Not configured** (default), Intune doesn't change or update this setting.

## Azure operational insights

- **Azure Operational Insights**: **Enable** collects, stores, and analyzes log data from Windows devices with Azure Operational Insights. Azure Operational Insights is part of the Microsoft Operations Manager suite. Enter the **Workspace ID** and **Workspace Key** to connect to Azure Operational insights.

    When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might not collect this data.

## Maintenance

These settings use the [SurfaceHub CSP](/en-us/windows/client-management/mdm/surfacehub-csp).

- **Maintenance window for updates**: **Enable** creates a maintenance window when updates can be installed. Enter the maintenance window **Start time**, and the **Duration in hours**, from 1-5 hours.

    When set to **Not configured** (default), Intune doesn't change or update this setting.

## Session

These settings use the [SurfaceHub CSP](/en-us/windows/client-management/mdm/surfacehub-csp).

- **Volume**: Enter the default volume value for a new session, from 0-100. When left blank, Intune doesn't change or update this setting. By default, the OS might set the volume to 45.
- **Screen timeout**: Enter the number of minutes until the Hub screen turns off.
- **Session timeout**: Enter the number of minutes until the session times out.
- **Sleep timeout**: Enter the number of minutes until the Hub enters sleep mode.
- **Session resume**: **Block** prevents users from resuming a session when the session times out. When set to **Not configured** (default), Intune doesn't change or update this setting.

## Wireless projection

These settings use the [SurfaceHub CSP](/en-us/windows/client-management/mdm/surfacehub-csp).

- **PIN for wireless projection**: **Require** forces users to enter a PIN before using the wireless projection features on the device. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Miracast wireless projection**: **Block** prevents using Miracast-enabled devices to project. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Miracast wireless projection channel**: Select the Miracast channel that establishes the connection.