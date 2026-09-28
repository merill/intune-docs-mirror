---
layout: Conceptual
title: Settings list for the Microsoft Edge security baseline in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-edge-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: aanavath
ms.subservice: protect
description: View a list of the settings in the Microsoft Intune security baseline for Microsoft Edge browser. This list includes the default values for settings as found in the default configuration of the baseline.
ms.date: 2025-01-09T00:00:00.0000000Z
ms.topic: reference
zone_pivot_groups: edge-baseline-versions
locale: en-us
document_id: f15af984-693c-1bf3-d502-ac76be984010
document_version_independent_id: f15af984-693c-1bf3-d502-ac76be984010
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-baselines/ref-edge-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-baselines/ref-edge-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-baselines/ref-edge-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 18a134c5-50dd-b95a-566c-d607c15cae55
---

# Settings list for the Microsoft Edge security baseline in Intune - Microsoft Intune | Microsoft Learn

This article is a reference for the settings that are available in the Microsoft Edge security baseline for Microsoft Intune.

In May 2023, the settings for the Microsoft Edge baselines updated to a new format. This article provides a reference for Microsoft Edge baselines version 85 and earlier. To view the settings reference for newer baselines, see [Microsoft Edge security baseline settings reference for Microsoft Intune](ref-v2-edge-settings).

## About this reference article

Each security baseline is a group of preconfigured Windows settings that help you apply and enforce granular security settings that the relevant security teams recommend. You can also customize each baseline you deploy to enforce only those settings and values you require. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration settings.

The details that display in this article are based on baseline version you select at the top of the article. For each version, this article displays:

- A list of each setting with its configuration as found in the default instance of that baseline version.
- When available, a link to the underlying configuration service provider (CSP) documentation or other related content from the relevant product group that provides context and possibly additional details for a settings use.

When a new version of a baseline becomes available, it replaces the previous version. Profile instances that you’ve created prior to the availability of a new version:

- Become read-only. You can continue to use those profiles but can't edit them to change their configuration.
- Can be updated to the current version. After you update a profile to the current baseline version, you can edit the profile to modify settings.

To learn more about using security baselines, see:

- [Use security baselines](overview)
- [Change the baseline version for a profile](configure-baselines#update-a-baseline-profile-to-the-latest-version)
- [Manage security baselines](configure-baselines)

::: zone pivot="edge-sept-2020"

## Microsoft Edge baseline for September 2020 (Edge version 85)

::: zone-end

::: zone pivot="edge-april-2020"

## Microsoft Edge baseline for April 2020 (Edge version 80)

::: zone-end

::: zone pivot="edge-october-2019"

## Microsoft Edge baseline for October 2019

Note

The Microsoft Edge baseline for October 2019 is a Public Preview.

::: zone-end

### Microsoft Edge

::: zone pivot="edge-sept-2020,edge-april-2020"

- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)

    - **Supported authentication schemes** Baseline defaults: Two items: *NTLM* and *Negotiate*
- **Default Adobe Flash setting** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowflash)

    - **Default Adobe Flash setting** Baseline default: *Block the Adobe Flash plugin*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)
- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all)** Baseline default: *Not configured by default. Manually add one or more Extension IDs*
- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*
- **Enable saving passwords to the password manager** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)
- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)
- **Enable site isolation for every site** Baseline default: *Enabled*

    *Microsoft Edge also supports [IsolateOrigins](/en-us/deployedge/microsoft-edge-policies#isolateorigins) policy that can isolate additional, finer-grained origins. Intune doesn't support configuring the IsolateOrigins policy.*
- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

    *This policy is available only on Windows instances that are joined to a Microsoft Active Director domain, or on Windows Pro or Enterprise instances that are enrolled for device management.*
- **Configure Microsoft Defender SmartScreen to block potentially unwanted apps** Baseline default: *Enabled*

    *This policy is available only on Windows instances that are joined to a Microsoft Active Director domain, or on Windows Pro or Enterprise instances that are enrolled for device management.*
- **Allow users to proceed from the SSL warning page** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)
- **Minimum SSL version enabled** Baseline default: *Enabled*

    - **Minimum SSL version enabled** Baseline default: *TLS 1.2*

::: zone-end

::: zone pivot="edge-october-2019"

- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Minimum SSL version enabled** Baseline default: *Enabled*

    - **Minimum SSL version enabled** Baseline default: *TLS 1.2*
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)
- **Allow users to proceed from the SSL warning page** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)
- **Default Adobe Flash setting** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowflash)

    - **Default Adobe Flash setting** Baseline default: *Block the Adobe Flash plugin*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)
- **Enable site isolation for every site** Baseline default: *Enabled*

    *Microsoft Edge also supports [IsolateOrigins](/en-us/deployedge/microsoft-edge-policies#isolateorigins) policy that can isolate additional, finer-grained origins. Intune doesn't support configuring the IsolateOrigins policy.*
- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)

    - **Supported authentication schemes** Baseline defaults: Two items: *NTLM* and *Negotiate*
- **Enable saving passwords to the password manager** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)
- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all)** Baseline default: *Not configured by default. Manually add one or more Extension IDs*
- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

    *This policy is available only on Windows instances that are joined to a Microsoft Active Director domain, or on Windows Pro or Enterprise instances that are enrolled for device management*.
- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*

::: zone-end

::: zone pivot="edge-sept-2020"

- **Allow certificates signed using SHA-1 when issued by local trust anchors (deprecated)** Baseline default: *Disabled*

    Important

    This setting is deprecated. It is currently supported but will become obsolete in a future release.

::: zone-end