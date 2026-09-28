---
layout: Conceptual
title: Settings list for the Local AI Agent Baseline - OpenClaw security baseline in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-openclaw-settings
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
description: View the settings in the Microsoft Intune security baseline for Local AI Agent Baseline - OpenClaw. This list includes the default values for settings as found in the default configuration of the baseline.
ms.date: 2026-05-29T00:00:00.0000000Z
ms.topic: reference
ai-usage: ai-assisted
locale: en-us
document_id: a2bff78d-776b-510f-c58c-6830c729c07a
document_version_independent_id: a2bff78d-776b-510f-c58c-6830c729c07a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-baselines/ref-openclaw-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-baselines/ref-openclaw-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-baselines/ref-openclaw-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 583397d6-4f63-6b2f-94d3-0152ed01cd65
---

# Settings list for the Local AI Agent Baseline - OpenClaw security baseline in Intune - Microsoft Intune | Microsoft Learn

This article is a reference for the settings that are available in the Local AI Agent Baseline - OpenClaw security baseline for Microsoft Intune.

This baseline limits the use of unauthorized local AI agents such as OpenClaw by configuring device settings that disrupt commonly used execution paths. Included firewall rules restrict outbound network communication from common local agent runtime environments like Node.js.

Important

These settings might not fully block all agent execution paths. This baseline includes controls that restrict runtime environments (for example, Windows Subsystem for Linux and Node.js) which can be leveraged by local agents. This baseline might also block other processes in addition to OpenClaw. Review and test each setting before deployment, and disable settings that have an unacceptable impact on legitimate workloads.

Tip

To identify devices that have local AI agents installed before deploying this baseline, use the [properties catalog](../../device-configuration/collect-device-properties) to collect **Local AI Agent** inventory data.

## About this reference article

Each security baseline is a group of preconfigured Windows settings that help you apply and enforce granular security settings that the relevant security teams recommend. You can also customize each baseline you deploy to enforce only those settings and values you require. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration settings.

This article displays:

- A list of each setting with its configuration as found in the default instance of that baseline version.
- When available, a link to the underlying configuration service provider (CSP) documentation or other related content from the relevant product group that provides context and possibly additional details for a settings use.

When a new version of a baseline becomes available, it replaces the previous version. Profile instances that were created before the availability of a new version:

- Become read-only. You can continue to use those profiles but can't edit them to change their configuration.
- Can be updated to the current version. After you update a profile to the current baseline version, you can edit the profile to modify settings.

To learn more about using security baselines, see:

- [Use security baselines](overview)
- [Change the baseline version for a profile](configure-baselines#update-a-baseline-profile-to-the-latest-version)
- [Manage security baselines](configure-baselines)

## Local AI Agent Baseline - OpenClaw (Preview), Version 1

### Windows Subsystem For Linux

- **Allow WSL1** Baseline default: *Enabled*[Learn more](/en-us/windows/wsl/compare-versions)
- **Allow the Windows Subsystem For Linux** Baseline default: *Enabled*[Learn more](/en-us/windows/wsl/about)

### Firewall

- **Firewall Rule Name** Baseline default: *Configured*[Learn more](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulename)

    This baseline includes two preconfigured firewall rules. Both rules block outbound TCP connections from Node.js executables to disrupt common execution paths used by OpenClaw.

#### Rule: block nodejs in LOCALAPPDATA folder

    | Property | Default value |
    | --- | --- |
    | [Enabled](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameenabled) | *Enabled* |
    | [Name](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamename) | block nodejs in LOCALAPPDATA folder |
    | [Interface Types](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameinterfacetypes) | *All* |
    | [File Path](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameappfilepath) | `%LOCALAPPDATA%\Programs\node\node.exe` |
    | [Network Types](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprofiles) | *FW\_PROFILE\_TYPE\_ALL* |
    | [Direction](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamedirection) | *The rule applies to outbound traffic* |
    | [Action](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameactiontype) | *Block* |
    | [Protocol](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprotocol) | *Configured* - 6 (TCP) |

#### Rule: block nodejs in ProgramFiles folder

    | Property | Default value |
    | --- | --- |
    | [Enabled](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameenabled) | *Enabled* |
    | [Name](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamename) | block nodejs in ProgramFiles folder |
    | [Interface Types](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameinterfacetypes) | *All* |
    | [File Path](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameappfilepath) | `%ProgramFiles%\nodejs\node.exe` |
    | [Network Types](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprofiles) | *FW\_PROFILE\_TYPE\_ALL* |
    | [Direction](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenamedirection) | *The rule applies to outbound traffic* |
    | [Action](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameactiontype) | *Block* |
    | [Protocol](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrulesfirewallrulenameprotocol) | *Configured* - 6 (TCP) |

    For details about firewall rule properties, see [Firewall CSP - FirewallRules](/en-us/windows/client-management/mdm/firewall-csp#mdmstorefirewallrules).