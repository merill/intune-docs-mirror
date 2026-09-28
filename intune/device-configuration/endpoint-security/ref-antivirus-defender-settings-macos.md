---
layout: Conceptual
title: macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-macos
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
description: See a list of the settings in the Microsoft Defender Antivirus profile for macOS. This profile is s part of Endpoint security Antivirus policy for macOS in Microsoft Intune.
ms.date: 2024-09-12T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: laarrizz
locale: en-us
document_id: e14bb25d-5b45-9645-2a7b-da98b26befcd
document_version_independent_id: e14bb25d-5b45-9645-2a7b-da98b26befcd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-antivirus-defender-settings-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 941d8b8a-2ac4-a4a8-a56d-2aa636cd9972
---

# macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune - Microsoft Intune | Microsoft Learn

View the *Microsoft Defender Antivirus* profile settings you can configure for Microsoft Defender for Endpoint for Mac in Microsoft Intune. For more information about these settings, see [Microsoft Defender for Endpoint for Mac](/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac) in the Windows documentation.

Learn about using [Endpoint security policies](manage-policies) in Intune.

## Cloud delivered protection preferences

For details about these settings, see the settings entry in [Set preferences for Microsoft Defender for Endpoint on macOS](/en-us/microsoft-365/security/defender-endpoint/mac-preferences) in the Microsoft Defender for Endpoint documentation.

- **Enable / disable cloud delivered protection**

    - *Not configured* (*default*)
    - *Enabled*
    - *Disabled*
- **Enable / disable automatic sample submissions**

    - *Not configured* (*default*)
    - *Enabled*
    - *Disabled*
- **Diagnostic collection level**

    - *Not configured* (*default*)
    - *Optional*
    - *Required*
- **Automatic security intelligence updates**

    - *Not configured* (*default*)
    - *Enabled*
    - *Disabled*

## Antivirus engine

For details about these settings, see the settings entry in [Set preferences for Microsoft Defender for Endpoint on macOS](/en-us/microsoft-365/security/defender-endpoint/mac-preferences) in the Microsoft Defender for Endpoint documentation.

- **Enable real-time protection (deprecated)** - This setting is replaced by *Enforcement level*.

    - *Not configured* (*default*)
    - *Enabled*
    - *Disabled*
- **Enable passive mode (deprecated)** - This setting is replaced by *Enforcement level*.

    - *Not configured* (*default*)
    - *Enabled*
    - *Disabled*
- **Scan history size**

    - *Not configured* (*default*)
    - *Configured* - When configured, specify a number of entries to keep in scan history.
- **Scan results retention**

    - *Not configured* (*default*)
    - *Configured* - When configured, specify the number of days that results are retained in the scan history on the device.
- **Exclusions merge**

    - *Not configured* (*default*)
    - *Admin\_only*
    - *Merge*
- **Scan exclusions**

    - *Configured* (*default*)
    - *Not configured*
- **Threat type settings**

    - *Configured* (*default*)
    - *Not configured*
- **Threat type settings merge**

    - *Not configured* (*default*)
    - *Admin\_only*
    - *Merge*
- **Allowed threats**

    - *Not configured* (*default*)
    - *Configured*
- **Disallowed threat actions**

    - *Not configured* (*default*)
    - *Configured*
- **Degree of parallelism for on-demand scans**

    - *Configured* (*default*) (2)
    - *Not configured*
- **Enable file hash computation**

    - *False* (*default*)
    - *True*
    - *Not configured*
- **Run a scan after definitions are updated**

    - *Enabled* (*default*)
    - *Disabled*
    - *Not configured*
- **Scanning inside archive files**

    - *False* (*default*)
    - *True*
    - *Not configured*
- **Enforcement level**

    - *Passive* (*default*)
    - *Real time*
    - *On Demand*

## Network protection

- **Enforcement level**
    - *Audit* (*default*)
    - *Disabled*
    - *Block*
    - *Not configured*

## Tamper protection

- **Enforcement level**
    - *Audit* (*default*)
    - *Disabled*
    - *Block*
    - *Not configured*

## User interface preferences

For details about these settings, see the settings entry in [Set preferences for Microsoft Defender for Endpoint on macOS](/en-us/microsoft-365/security/defender-endpoint/mac-preferences) in the Microsoft Defender for Endpoint documentation.

- **Control sign-in to consumer version**

    - *Enabled* (*default*)
    - *Disabled*
    - *Not configured*
- **Show / hide status menu icon**

    - *Disabled* (*default*)
    - *Enabled*
    - *Not configured*
- **User initiated feedback**

    - *Enabled* (*default*)
    - *Disabled*
    - *Not configured*