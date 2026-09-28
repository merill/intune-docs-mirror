---
layout: Conceptual
title: Endpoint Protection Client Help - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-client-help
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about features and enhancements in Endpoint Protection that better help you protect your computer from threats.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ea128a58-46a0-65ce-50bb-0d2bd943101d
document_version_independent_id: 80e06f7f-98cb-baa0-8cfd-cef013a96966
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-protection-client-help.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-protection-client-help
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-protection-client-help.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 05037891-d61c-194a-7472-902f60f31b1c
---

# Endpoint Protection Client Help - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This version of Windows Defender or Endpoint Protection includes the following features to help protect your computer from threats:

- **Windows Firewall integration.** Endpoint Protection setup enables you to turn on or off Windows Firewall.
- **Network Inspection System.** This feature enhances real-time protection by inspecting network traffic to help proactively block exploitation of known network-based vulnerabilities.
- **Protection engine.** Real-time protection finds and stops malware from installing or running on your PC. The updated engine offers enhanced detection and cleanup capabilities with better performance.

Windows Defender comes as part of the operating system starting in Windows 10. On earlier versions of Windows, your administrator can provide either Windows Defender or Endpoint Protection using management software.

You can also find a list of [frequently asked questions for Windows Defender and Endpoint Protection](endpoint-protection-client-faq). For help troubleshooting, see [Troubleshooting Windows Defender or Endpoint Protection client](troubleshoot-endpoint-client). For a list of new features, see [What's new Windows Defender client](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## Windows Firewall integration

Windows Firewall can help prevent attackers or malicious software from gaining access to your computer through the Internet or a network. Now when you install Endpoint Protection, the installation wizard verifies that Windows Firewall is turned on. If you have intentionally turned off Windows Firewall, you can avoid turning it on by clearing a check box. You can change your Windows Firewall settings at any time via the System and Security settings in Control Panel.

## Network Inspection System

Attackers are increasingly carrying out network-based attacks against exposed vulnerabilities before software vendors can develop and distribute security updates. Studies of vulnerabilities show that it can take a month or longer from the time of an initial attack report before a suitable security update is developed, tested, and released. This gap in protection leaves many computers vulnerable to attacks and exploitation for a substantial period of time. Network Inspection System works with real-time protection to better protect you against network-based attacks by greatly reducing the timespan between vulnerability disclosures and update deployment from weeks to a few hours.

## Award-winning protection engine

Under the hood of Windows Defender or Endpoint Protection is its award-winning protection engine that is updated regularly. The engine is backed by a team of antimalware researchers from the Microsoft Malware Protection Center, providing responses to the latest malware threats 24 hours a day.

## Windows Defender settings

Windows Defender settings enable settings that help protect your PC from malicious software. Your administrator might manage some Windows Defender settings for you. You can manage others using the Windows Defender settings. We recommend you enable Windows Defender settings to help protect your PC and data.

To view Windows Defender settings, search for `Windows Defender` on your PC. Open **Windows Defender** and select **Settings**. Windows Defender settings include:

- **Real-time protection** - Find and stop malware from installing or running on your PC.
- **Cloud-based Protection** - Windows Defender sends info to Microsoft about potential security threats.
- **Automatic sample submission** - Allow Windows Defender to send samples of suspicious files to Microsoft to help improve malware detection.
- **Exclusions** - You can exlude specific files, folders, file extensions, or processes from Windows Defender scanning.
- **Enhanced notification** - Enables notifications that inform about the health of your PC. Even **Off** you will receive critical notifications.
- **Windows Defender Offline** - You can run Windows Defender Offline to help find and remove malicious software. This scan will restart your PC and will take about 15 minutes.

### See also

[Endpoint Protection client frequently asked questions](endpoint-protection-client-faq)[Troubleshooting Windows Defender or Endpoint Protection client](troubleshoot-endpoint-client)