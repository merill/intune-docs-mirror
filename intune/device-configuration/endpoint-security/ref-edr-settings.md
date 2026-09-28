---
layout: Conceptual
title: Intune endpoint security Endpoint detection and response settings - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-edr-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Endpoint security Endpoint detection and response policy settings for deprecated profiles in Microsoft Intune
ms.date: 2025-03-28T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
locale: en-us
document_id: 491d9c57-e8c8-3e4b-2b4d-e17494e0ca13
document_version_independent_id: 491d9c57-e8c8-3e4b-2b4d-e17494e0ca13
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-edr-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-edr-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-edr-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 9418057a-c875-cbcc-3202-f1e1d828b07c
---

# Intune endpoint security Endpoint detection and response settings - Microsoft Intune | Microsoft Learn

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

The information in this article applies only to the settings in the Endpoint detection and response profile for the *Windows 10 and later* platform for endpoint security Endpoint detection and response policy.

Beginning on April 5, 2022, the *Windows 10 and later* platform was replaced by the *Windows* platform. Although you can no longer create a new instance of this older profile, you can continue to edit and use an existing instances of this profile. The settings details in this article apply only to the deprecated profiles.

View the settings you can configure in profiles for [Endpoint detection and response policy](deploy-edr) in the endpoint security node of Intune.

Applies to:

- Windows

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Supported platforms and profiles:

- **Windows**: Use this platform for policy you deploy to Windows devices managed with Intune.

    - Profile: **Endpoint detection and response (MDM)**
- **Windows (ConfigMgr)**: Use this platform for policy you deploy to devices managed by Configuration Manager.

    - Profile: **Endpoint detection and response (ConfigMgr)**

## Endpoint detection and response (MDM)

**Endpoint detection and response**:

- **Microsoft Defender for Endpoint client configuration package type**

    Upload a signed configuration package that will be used to onboard the Microsoft Defender for Endpoint client.

    - **Not configured** (*default*)
    - **Onboarding blob**
    - **Offboarding blob**

    When set to *Onboarding blob*, you can configure the following settings:

    - **Defender for Endpoint onboarding blob** Click **Select onboarding file** to open the *Select onboarding File* pane, where you specify a `.onboarding` file.

    When set to *Offboarding blob*, you can configure the following settings:

    - **Defender for Endpoint offboarding blob** Click **Select offboarding file** to open the *Select offboarding File* pane, where you specify a `.offboarding` file.
- **Sample sharing for all files**

    Returns or sets the Microsoft Defender for Endpoint Sample Sharing configuration parameter. Sample Sharing sends a file to Microsoft for deep analysis. Organizations can disable sample sharing on specific devices that are considered too sensitive.

    - **Not configured** (*default*)
    - **Yes**
- **Expedite telemetry reporting frequency**

    - **Not configured** (*default*)
    - **Yes** - Increase the Microsoft Defender for Endpoint telemetry reporting frequency.

## Endpoint detection and response (ConfigMgr)

**Endpoint detection and response**:

- **Sample sharing for all files**

    Returns or sets the Microsoft Defender for Endpoint Sample Sharing configuration parameter.

    - **Not configured** (*default*)
    - **Yes**
- **Expedite telemetry reporting frequency**

    - **Not configured** (*default*)
    - **Yes** - Increase the Microsoft Defender for Endpoint telemetry reporting frequency.