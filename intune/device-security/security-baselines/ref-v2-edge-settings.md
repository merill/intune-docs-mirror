---
layout: Conceptual
title: List of settings for the Microsoft Edge security baseline in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-v2-edge-settings
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
description: View a list of the settings in the Microsoft Intune security baseline version 112 and later, for the Microsoft Edge browser. This list includes the default values for settings as found in the default configuration of the baseline.
ms.date: 2026-04-27T00:00:00.0000000Z
ms.topic: reference
zone_pivot_groups: dcv2-edge-baselines
locale: en-us
document_id: c5610042-5b89-4bb2-fe09-69609b2dda91
document_version_independent_id: c5610042-5b89-4bb2-fe09-69609b2dda91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-baselines/ref-v2-edge-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-baselines/ref-v2-edge-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-baselines/ref-v2-edge-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 48be8f6b-af3b-968e-45d8-4430e545e4d0
---

# List of settings for the Microsoft Edge security baseline in Intune - Microsoft Intune | Microsoft Learn

This article is a reference for the settings that are available in the Microsoft Edge security baseline for Microsoft Intune and applies to versions of that baseline that released in May 2023 or later.

If you use a security baseline for Microsoft Edge version 85 or earlier, see [List of the settings in the Microsoft Edge security baseline in Intune](ref-edge-settings).

Note

Beginning in May 2023, all new security baseline versions use a new settings format that replaces previous versions. While the last version instance for a baseline that uses the older setting format remains available to use, the older format will no longer receive updates for new settings, or updated default configurations.

## About this reference article

Each security baseline is a group of preconfigured Windows settings that help you apply and enforce granular security settings that the relevant security teams recommend. You can also customize each baseline you deploy to enforce only those settings and values you require. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration settings.

The details that display in this article are based on baseline version you select at the top of the article. For each version, this article displays:

- A list of each setting with its configuration as found in the default instance of that baseline version.
- When available, a link to the underlying configuration service provider (CSP) documentation or other related content from the relevant product group that provides context and possibly additional details for a settings use.

When a new version of a baseline becomes available, it replaces the previous version. Profile instances that you’ve created prior to the availability of a new version:

- Become read-only. You can continue to use those profiles but can't edit them to change their configuration.

    Tip

    Because the new baselines versions introduced in May 2023 or later exist side-by-side with the last baseline version from the older format, baselines for the last available version of that older format remain accessible to use and to edit.
- Can be updated to the current version. After you update a profile to the current baseline version, you can edit the profile to modify settings.

To learn more about using security baselines, see:

- [Use security baselines](overview)
- [Change the baseline version for a profile](configure-baselines#update-a-baseline-profile-to-the-latest-version)
- [Manage security baselines](configure-baselines)

::: zone pivot="edge-v139"

## Microsoft Edge baseline for version 139 (April 2026)

For information about the most recent baseline versions and settings from Microsoft, including versions of this baseline that might not be available through Intune, download the [Microsoft Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319) from the Microsoft Download Center.

### Microsoft Edge

- **Allow unconfigured sites to be reloaded in Internet Explorer mode** Baseline default: *Disabled*
- **Allow users to proceed from the HTTPS warning page** Baseline default: *Disabled*
- **Automatically open downloaded MHT or MHTML files from the web in Internet Explorer mode** Baseline default: *Disabled*
- **Dynamic Code Settings** Baseline default: *Enabled*

    - **Dynamic Code Settings (Device)** Baseline default: *Prevent the browser process from creating dynamic code*
- **Enable Application Bound Encryption** Baseline default: *Enabled*
- **Enable browser legacy extension point blocking** Baseline default: *Enabled*
- **Enable site isolation for every site** Baseline default: *Enabled*
- **Show the Reload in Internet Explorer mode button in the toolbar** Baseline default: *Disabled*
- **Specifies whether SharedArrayBuffers can be used in a non cross-origin-isolated context** Baseline default: *Disabled*
- **Allow software WebGL fallback using SwiftShader** Baseline default: *Disabled*

### Extensions

- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all) (Device)** Baseline default: \*

### HTTP authentication

- **Allow Basic authentication for HTTP** Baseline default: *Disabled*
- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)

    - **Supported authentication schemes (Device)** Baseline default: *ntlm,negotiate*

### Native Messaging

- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*

### SmartScreen settings

- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)
- **Configure Microsoft Defender SmartScreen to block potentially unwanted apps** Baseline default: *Enabled*
- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

### Typosquatting Checker settings

- **Configure Edge Website Typo Protection** Baseline default: *Enabled*

::: zone-end

::: zone pivot="edge-v128"

## Microsoft Edge baseline for version 128 (January 2025)

For information about the most recent baseline versions and settings from Microsoft, including versions of this baseline that might not be available through Intune, download the [Microsoft Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319) from the Microsoft Download Center.

- **Allow unconfigured sites to be reloaded in Internet Explorer mode** Baseline default: *Disabled*
- **Allow users to proceed from the HTTPS warning page** Baseline default: *Disabled*
- **Automatically open downloaded MHT or MHTML files from the web in Internet Explorer mode** Baseline default: *Disabled*
- **Dynamic Code Settings** Baseline default: *Enabled*

    - **Dynamic Code Settings (Device)** Baseline default: *Default dynamic code settings*
- **Enable Application Bound Encryption** Baseline default: *Enabled*
- **Enable browser legacy extension point blocking** Baseline default: *Enabled*
- **Enable site isolation for every site** Baseline default: *Enabled*
- **Show the Reload in Internet Explorer mode button in the toolbar** Baseline default: *Disabled*
- **Specifies whether SharedArrayBuffers can be used in a non cross-origin-isolated context** Baseline default: *Disabled*

### Extensions

- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all) (Device)** Baseline default: \*

### HTTP authentication

- **Allow Basic authentication for HTTP** Baseline default: *Disabled*
- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)

    - **Supported authentication schemes (Device)** Baseline default: *ntlm,negotiate*

### Native Messaging

- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*

### Private Network Request Settings

- **Specifies whether to allow insecure websites to make requests to more-private network endpoints** Baseline default: *Disabled*

### SmartScreen settings

- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)
- **Configure Microsoft Defender SmartScreen to block potentially unwanted apps** Baseline default: *Enabled*
- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

### Typosquatting Checker settings

- **Configure Edge Typo Protection** Baseline default: *Enabled*

::: zone-end

::: zone pivot="edge-v117"

## Microsoft Edge baseline for version 117 (November 2023)

For information about the most recent baseline versions and settings from Microsoft, including versions of this baseline that might not be available through Intune, download the [Microsoft Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319) from the Microsoft Download Center.

- **Allow unconfigured sites to be reloaded in Internet Explorer mode** Baseline default: *Disabled*
- **Allow users to proceed from the HTTPS warning page** Baseline default: *Disabled*
- **Automatically open downloaded MHT or MHTML files from the web in Internet Explorer mode** Baseline default: *Disabled*
- **Enable browser legacy extension point blocking** Baseline default: *Enabled*
- **Enable site isolation for every site** Baseline default: *Enabled*
- **Enhance images enabled** Baseline default: *Disabled*
- **Force WebSQL to be enabled** Baseline default: *Disabled*
- **Show the Reload in Internet Explorer mode button in the toolbar** Baseline default: *Disabled*
- **Specifies whether SharedArrayBuffers can be used in a non cross-origin-isolated context** Baseline default: *Disabled*

### Extensions

- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all) (Device)** Baseline default: *\**

### HTTP authentication

- **Allow Basic authentication for HTTP** Baseline default: *Disabled*
- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)

### Native Messaging

- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*

### Private Network Request Settings

- **Specifies whether to allow insecure websites to make requests to more-private network endpoints** Baseline default: *Disabled*

### SmartScreen settings

- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)
- **Configure Microsoft Defender SmartScreen to block potentially unwanted apps** Baseline default: *Enabled*
- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)
- **Configure Edge TyposquattingChecker** Baseline default: *Enabled*

::: zone-end

::: zone pivot="edge-v112"

## Microsoft Edge baseline for version 112 (May 2023)

For information about the most recent baseline versions and settings from Microsoft, including versions of this baseline that might not be available through Intune, download the [Microsoft Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319) from the Microsoft Download Center.

- **Allow unconfigured sites to be reloaded in Internet Explorer mode** Baseline default: *Disabled*
- **Allow users to proceed from the HTTPS warning page** Baseline default: *Disabled*
- **Enable browser legacy extension point blocking** Baseline default: *Enabled*
- **Enable site isolation for every site** Baseline default: *Enabled*
- **Enhance images enabled** Baseline default: *Disabled*
- **Force WebSQL to be enabled** Baseline default: *Disabled*
- **Minimum TLS version enabled** Baseline default: *Enabled*

    - **Minimum SSL version enabled (Device)** Baseline default: *TLS 1.2*
- **Show the Reload in Internet Explorer mode button in the toolbar** Baseline default: *Disabled*
- **Specifies whether SharedArrayBuffers can be used in a non cross-origin-isolated context** Baseline default: *Disabled*

### Extensions

- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all) (Device)** Baseline default: *\**

### HTTP authentication

- **Allow Basic authentication for HTTP** Baseline default: *Disabled*
- **Supported authentication schemes** Baseline default: *Enabled*[Learn more](/en-us/deployedge/microsoft-edge-policies#authschemes)
- **Supported authentication schemes (Device)** Baseline default: *ntlm,negotiate*

### Native Messaging

- **Allow user-level native messaging hosts (installed without admin permissions)** Baseline default: *Disabled*

### Password manager and protection

- **Enable saving passwords to the password manager** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)

### Private Network Request Settings

- **Specifies whether to allow insecure websites to make requests to more-private network endpoints** Baseline default: *Disabled*

### SmartScreen settings

- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)
- **Configure Microsoft Defender SmartScreen to block potentially unwanted apps** Baseline default: *Enabled*
- **Prevent bypassing Microsoft Defender SmartScreen prompts for sites** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)
- **Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

::: zone-end

- [Learn about security baselines](overview)
- [Avoid conflicts](overview#avoid-conflicts)
- [Troubleshoot policies and profiles in Intune](/en-us/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune)