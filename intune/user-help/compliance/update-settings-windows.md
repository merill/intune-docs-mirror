---
layout: Conceptual
title: Company Portal device setting requirements for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/update-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn more about Intune Company Portal device setting requirements for Windows OS.
ms.date: 2024-08-05T00:00:00.0000000Z
ms.reviewer: madakeva
locale: en-us
document_id: ad076d60-97cf-f39c-ee2f-6b09f51e73aa
document_version_independent_id: ad076d60-97cf-f39c-ee2f-6b09f51e73aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/update-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/update-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/update-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4acc19c5-215e-fd22-fcb6-2438d85d4dd0
---

# Company Portal device setting requirements for Windows - Microsoft Intune | Microsoft Learn

This article describes the Windows device setting requirements in Intune Company Portal. Company Portal enforces these requirements on behalf of your workplace or school to ensure your device is secure while accessing their network. Requirements are specific to each organization. You only need to update the device settings that Company Portal flags.

## Update operating system

To get the latest updates for Windows, see [Microsoft Support: Get the latest Windows update](https://support.microsoft.com/windows/get-the-latest-windows-update-7d20e88c-0568-483a-37bc-c3885390d212).

We recommend keeping the operating system (OS) on work and school devices up-to-date. Before updating a device, back up all of the information on it. Keep a backup so that you can recover your data if something interrupts the update, or transfer your information to a replacement device.

## Operating system isn't supported

The operating system (OS) version running on your device isn't supported. The current version of Windows might not work with your organization's apps, tools, or other internal infrastructure. To resolve this issue, either upgrade or downgrade to an OS version supported by your organization. OS requirements vary by organization. Contact your IT support person to find out what requirements you need to meet.

For information about how to upgrade to Windows 11, see:

- [Upgrade to Windows 11: FAQ](https://support.microsoft.com/windows/upgrade-to-windows-11-faq-fb6206a2-1a0f-448a-80f1-8668ee5b2bf9)
- [Getting ready for the Windows 11 upgrade](https://support.microsoft.com/windows/getting-ready-for-the-windows-11-upgrade-eb50813f-c7da-4cf8-89a3-6ba0d33b2773)

## Enable anti-malware protection

Anti-malware is an important factor in making sure your device is protected. To meet this compliance requirement, enable the anti-malware software and features required by your organization. On devices running more recent versions of Windows, the built-in anti-malware software is Microsoft Defender Antivirus.

Remember to only download apps from verified sources, such as the Company Portal app and the Microsoft Store. For more information about anti-malware for Windows, see [Microsoft Support: Getting started with anti-malware in Microsoft Defender](https://support.microsoft.com/topic/getting-started-with-anti-malware-in-microsoft-defender-f5219ae5-abb7-4985-a149-1ec1bb304eda).

## Enable Window Code Integrity

Contact your IT support person to enable code integrity on your work or school device. Code integrity is a threat protection feature that checks the drivers and system files on your device for signs of corruption or malicious software. For it to work on your device, another security feature called *Secure Boot* must be enabled. Your IT support person can also help you enable Secure Boot, which will in turn trigger code integrity the next time you start up your device.

## Turn on Windows Defender Firewall

Windows Defender Firewall helps prevent hackers and malicious software from gaining access to your work or school device through the internet or a network. Your organization might require you to turn it on before you can access their network resources.

For more information and how-to instructions, see [Microsoft Support: Turn Microsoft Defender Firewall on or off](https://support.microsoft.com/windows/turn-microsoft-defender-firewall-on-or-off-ec0844f7-aebd-0583-67fe-601ecf5d774f) on Microsoft Support.

## Access point restrictions not set up

Your company applied access point restrictions on your device. This setting requires the Company Portal app to verify a few network settings on your device. Tap **Resolve** and wait while the Company Portal app checks for an approved network connection.

## Not connected to an approved network

Your device is connected to a network that isn't approved for work access. While connected to this network, you can't access work email, apps, and other protected resources. To meet this compliance requirement, connect to a company-approved network. Then tap **Resolve** in Company Portal to retry.

## Restrictions couldn't be enforced

Company Portal can't determine if your device is connected to an approved network. This error could be a result of poor network connectivity, low battery, battery saver mode, or a Company Portal error. To resolve, verify that you have a strong network reception. Turn off battery saver mode and make sure your battery life has at least 30% remaining. Then tap **Resolve** in Company Portal to retry.

## Enable Secure Boot

[Secure Boot](/en-us/windows/security/operating-system-security/system-security/secure-the-windows-10-boot-process#secure-boot) is a security standard developed by members of the PC industry to help ensure that a device boots using only software that's trusted by the original equipment manufacturer (OEM). Your organization might require you to enable it. We recommend reaching out to your IT support person for help with enabling Secure Boot on a work or school device.

Secure Boot settings are available in Windows Security and UEFI BIOS settings. For information about accessing the UEFI menu on a Surface device, see [Manage Surface UEFI settings](/en-us/surface/manage-surface-uefi-settings#open-surface-uefi-menu). For information about how to boot other devices into UEFI BIOS mode, see the manufacturer's documentation.

## Turn on virus and threat protection

Microsoft Defender Antivirus is an antivirus software included in Windows that protects against viruses, malware, and other threats. Your organization might require you to turn on specific antivirus features on your device before you can access their network.

- Turn on real-time protection: Real-time protection enables Microsoft Defender Antivirus to scan for threats on your device. To turn on real-time protection, go to **Start** &gt; **Windows Security** &gt; **Virus & threat protection**.

- Turn on cloud-delivered protection: On your device, go to **Start** &gt; **Windows Security** &gt; **Virus & threat protection**. Turn on cloud-delivered protection.

- Update antivirus definitions: On your device, go to **Start** &gt; **Windows Security** &gt; **Virus & threat protection**. Then check for new protection updates. If you don't see the option to check for updates, turn on real-time protection and cloud-delivered protection, and then try again.

For more information, see [Microsoft Support: Virus & threat protection in Windows Security](https://support.microsoft.com/windows/virus-threat-protection-in-windows-security-1362f4cd-d71a-b52a-0b66-c2820032b65e).

## Change User Access Control setting

The User Access Control settings prevent potentially harmful programs and software from making changes to your device. To meet this compliance requirement, adjust User Access Control so that your device has more protection. User Access Control settings are in Control Panel under **System and Security**. For more information, see [Microsoft Support: User Account Control settings](https://support.microsoft.com/windows/user-account-control-settings-d5b2046b-dcb8-54eb-f732-059f321afe18).