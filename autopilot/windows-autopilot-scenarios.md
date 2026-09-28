---
layout: Conceptual
title: Windows Autopilot scenarios and capabilities | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/windows-autopilot-scenarios
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Follow along with several typical Windows Autopilot deployment scenarios, such as redeploying a device in a business-ready state.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: article
locale: en-us
document_id: af443b25-ab57-77ef-9689-556ee535467c
document_version_independent_id: af443b25-ab57-77ef-9689-556ee535467c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/windows-autopilot-scenarios.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: windows-autopilot-scenarios
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/windows-autopilot-scenarios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8a6157f0-0c52-bea7-09e9-82719980c15d
---

# Windows Autopilot scenarios and capabilities | Microsoft Learn

## Scenarios

Windows Autopilot supports a growing list of scenarios that organizations commonly need. These needs vary based on:

- Organization type.
- Progress moving to the latest version of Windows.
- The state of transitioning to [modern management](/en-us/windows/client-management/manage-windows-10-in-your-organization-modern-management).

The following Windows Autopilot scenarios are described in this guide:

| **Scenario** | **Description** |
| --- | --- |
| [Windows Autopilot user-driven mode](user-driven) | Deploy and configure devices so that an end user can set it up for themselves. |
| [Windows Autopilot self-deploying mode](self-deploying) | Deploy devices to be automatically configured for shared use, as a kiosk, or as a digital signage device. |
| [Windows Autopilot Reset](windows-autopilot-reset) | Redeploy a device in a business-ready state. |
| [Pre-provisioning](pre-provision) | Pre-provision a device with up-to-date applications, policies, and settings. |
| [Windows Autopilot for existing devices](existing-devices) | Deploy Windows on an existing Windows device. |

These scenarios are summarized in the following video:

## Windows Autopilot capabilities

### Temporary Access Pass

Organizations using [Temporary Access Pass](/en-us/azure/active-directory/authentication/howto-authentication-temporary-access-pass) can use this feature with Windows Autopilot Microsoft Entra join user driven, pre-provisioning, and self-deploying mode for shared devices. The native Windows sign-in credential provider doesn't support Temporary Access Pass so it requires the enablement of WebSign-in. To enable this feature in the organization, follow the Configuration Service Provider (CSP) details outlined in [Policy CSP - Authentication](/en-us/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin). This feature isn't supported with Windows Autopilot Microsoft Entra hybrid join devices and isn't applicable on self-deploying mode kiosks.

### Cortana voiceover and speech recognition during OOBE

In Windows 10, Cortana voiceover and speech recognition during the out-of-box experience (OOBE) is **DISABLED** by default. This default applies to all Windows Pro, Education, and Enterprise editions. This feature isn't available in versions of Windows after Windows 10.

Cortana voiceover and speech recognition can be enabled during OOBE by creating the registry key value `EnableVoiceForAllEditions` in the following registry key:

> 
> `HKLM\Software\Microsoft\Windows\CurrentVersion\OOBE\`

This registry key value doesn't exist by default.

The key value is a DWORD with **0** = disabled and **1** = enabled.

| **Value** | **Description** |
| --- | --- |
| **0** | Cortana voiceover is disabled |
| **1** | Cortana voiceover is enabled |
| No value | Device falls back to default behavior of the edition |

To change this key value, use the Windows Configuration Designer (WCD) tool to create as PPKG as documented in [EnableCortanaVoice](/en-us/windows/configuration/wcd/wcd-oobe#enablecortanavoice).

For more information, see [Cortana voice support](/en-us/windows-hardware/customize/desktop/cortana-voice-support).

Note

Microsoft deprecated the Windows Cortana standalone app. The Cortana productivity assistant is still available. For more information on deprecated features on Windows client, go to [Deprecated features for Windows client](/en-us/windows/whats-new/deprecated-features).

### BitLocker encryption

With Windows Autopilot, BitLocker encryption settings can be configured to apply before automatic encryption is started. For more information, see [Setting the BitLocker encryption algorithm for Windows Autopilot devices](bitlocker).