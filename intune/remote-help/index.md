---
layout: Conceptual
title: Use Remote Help to Assist Users Authenticated by your Organization - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/remote-help/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: suite
description: With the Remote Help app, provide remote assistance to authenticated users who also run the Remote Help app.
ms.date: 2026-08-13T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
ms.reviewer: karawang
locale: en-us
document_id: a6e6fd3a-a10b-9cb7-bc63-6ec1e28ec718
document_version_independent_id: a6e6fd3a-a10b-9cb7-bc63-6ec1e28ec718
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/remote-help/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote-help/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/remote-help/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 52f30159-ec75-87c3-dbca-7f9c3d2c8eee
---

# Use Remote Help to Assist Users Authenticated by your Organization - Microsoft Intune | Microsoft Learn

Microsoft Intune Remote Help is a cloud-based remote support solution that allows IT support teams to connect securely to an end-user's device for real-time assistance. It enables organizations to provide remote troubleshooting and guidance with enterprise security controls in place. Remote Help distinguishes between helpers (support personnel) and sharers (end users sharing their screen), both of whom must sign in with corporate Entra ID accounts for each session. This requirement means Remote Help only works within your organization's tenant – helpers can't assist users in another tenant or external organization.

## Remote Help capabilities

The Remote Help app supports the following capabilities in general across the supported platforms.

- **Enable Remote Help for your tenant**: By default, Remote Help isn't enabled for Intune tenants. If you choose to turn on Remote Help, its use is enabled tenant-wide. Remote Help must be enabled before users can be authenticated through your tenant when using Remote Help.

    [![A screenshot of the tenant administration screen where you can enable Remote Help.](media/index/remote-help-enable.png)](media/index/remote-help-enable-expanded.png#lightbox)
- **Requires Organization login**: To use Remote Help, both the helper and the sharer must sign in with a Microsoft Entra account from your organization. You can't use Remote Help to assist users who aren't members of your organization.

    ![Screenshot of Remote Help requiring an organizational account.](media/index/remote-help-organizational-account.png)
- **Compliance Warnings**: Before a helper connects to a user's device, helpers see a noncompliance warning about that device if it's not compliant with its assigned policies.
- **Role-based access control**: Admins can set RBAC rules that determine the scope of a helper's access, such as:

    - The users who can help others and the range of actions they can do while providing help. For example, who can run elevated privileges while helping.
    - The users who can only view a device, and who can request full control of the session while assisting others.
- **Monitor active Remote Help sessions, and view details about past sessions**: In the Microsoft Intune admin center, you can view reports that include details about who helped who, on what device, and for how long. You can also find details about active sessions. An administrator can also reference audit log sessions created for Remote Help in Intune under **Tenant Administration** &gt; **Audit Logs**.

    For unenrolled devices, auditing the Remote Help sessions is limited.
- **Web app for sharers** - In situations where the Sharer needs assistance but is unable to install the native application for macOS or Windows, the Sharer can use the Web App to share their screen to a helper. This web app provides view only capabilities to the helper, allowing them to guide the user through resolving issues.

## Platform-specific capabilities

# [Windows](#tab/windows)
- **Elevation**: Allows helpers to enter UAC credentials when prompted on the sharer's device. Enabling elevation also allows the helper to view and control the sharer's device when the sharer grants the helper access.

    [![Screenshot of the prompt to enable elevation support during a remote help session on Windows.](media/index/remote-help-windows-elevation.png)](media/index/remote-help-windows-elevation-expanded.png#lightbox)
- **Remote launch**: Allows helpers to launch Remote Help on the helper and sharer's device from Intune by sending a notification to the sharer's device.

    ![A screenshot of the sharer's computer showing the prompt to start a Remote Help session using the Remote Launch feature.](media/index/remote-help-windows-remote-launch.png)
- **Unattended control: Remote sign-in**: Allows an authorized helper to sign in to a corporate Windows device with their own credentials and troubleshoot without requiring an end user to be present or signed in. Unlike attended control, which displays an active user's session, unattended remote sign-in creates a separate authenticated Windows session governed by user authentication, Intune role-based access control (RBAC), and auditing. This capability is initiated from the Microsoft Intune admin center and applies only to physical, corporate-owned, Intune-managed Windows devices.

    [![Screenshot of the Remote Help control session type dialog with unattended control selected.](media/index/remote-help-unattended-windows.png)](media/index/remote-help-unattended-windows.png#lightbox)
- **Optional support for unenrolled devices**: This setting is turned off by default. Enabling this option allows help to be provided to devices that aren't enrolled in Intune. This setting doesn't apply to devices used by helpers or to unattended control, which supports only Intune-enrolled devices.

    ![A screenshot of the option to enable unenrolled devices](media/index/remote-help-unenrolled.png)
- **Conditional access support**: You can use Conditional Access policies to control how helpers and sharers access Remote Help. For example, you can require multifactor authentication (MFA) for helpers or restrict access to specific locations or compliant devices. These policies apply to Remote Help sessions that are accepted by an end user, who participates in the session, and don't apply to unattended access.
- **Chat functionality**: Remote Help includes enhanced chat that maintains a continuous thread of all messages. This chat supports special characters and other languages including Chinese and Arabic. Chat functionality applies to Remote Help sessions that are accepted by an end user, who participates in the session, and doesn't apply to unattended access. For more information, see [Supported languages for chat](plan#supported-languages-for-chat).
- **Web app for sharers** - In situations where the Sharer needs assistance but is unable to install the native application for macOS, the Sharer can use the Web App to share their screen to a helper. This web app provides view only capabilities to the helper, allowing them to guide the user through resolving issues.

# [macOS](#tab/macos)
- **Conditional access support**: You can use Conditional Access policies to control how helpers and sharers access Remote Help. For example, you can require multifactor authentication (MFA) for helpers or restrict access to specific locations or compliant devices.
- **Chat functionality**: Remote Help includes enhanced chat that maintains a continuous thread of all messages. This chat supports special characters and other languages including Chinese and Arabic. For more information on languages supported, see [Languages Supported](plan#supported-languages-for-chat).
- **Optional support for unenrolled devices**: This setting is turned off by default. For Windows and macOS devices, enabling this option allows help to be provided to devices that aren't enrolled in Intune. This setting doesn't apply to devices used by helpers.

    ![A screenshot of the opion to enable unenrolled devices](media/index/remote-help-unenrolled.png)

# [Android](#tab/android)
- **Unattended control**: Helpers can connect to Android devices without requiring the sharer to accept the connection each time. This capability requires the Android device to be enrolled in Intune as an Android Enterprise dedicated device.

    [![Screenshot of an unattended Remote Help session on Android](media/index/remote-help-android-unattended.png)](media/index/remote-help-android-unattended-expanded.png#lightbox)

---

## Demos and Videos

# [Windows](#tab/windows)
The [Remote Help](https://regale.cloud/Microsoft/viewer/1746/remote-help/index.html#/0/0) interactive demo walks you through scenarios step-by-step with interactive annotations and navigation controls.

# [macOS](#tab/macos)
Use the interactive demos to explore Remote Help on macOS:

- [macOS native experience](https://regale.cloud/microsoft/play/1746/remote-help#/7/0)
- [macOS web app experience](https://regale.cloud/microsoft/play/1746/remote-help#/6/0)

# [Android](#tab/android)
Check back in this space for demos and videos of Remote Help for Android.

---