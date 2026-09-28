---
layout: Conceptual
title: Using Windows virtual machines with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/windows-virtual-machines
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: This article describes the general guidelines for using Windows virtual machines with Microsoft Intune
ms.date: 2025-02-13T00:00:00.0000000Z
ms.topic: article
ms.reviewer: priyar
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 5fce6601-3a0f-eb01-fec0-49331605a6af
document_version_independent_id: 5fce6601-3a0f-eb01-fec0-49331605a6af
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/windows-virtual-machines.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/windows-virtual-machines
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/windows-virtual-machines.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: 25b332b2-2d2d-ca6b-0f86-207b08306b3f
---

# Using Windows virtual machines with Microsoft Intune - Microsoft Intune | Microsoft Learn

Intune supports managing virtual machines running Windows Enterprise with certain limitations. Intune management doesn't depend on, or interfere with Azure Virtual Desktop management of the same virtual machine.

## Enrollment

- We recommend that you don't use Intune to manage on-demand, session-host virtual machines, also known as non-persistent virtual desktop infrastructure (VDI). Each VM must be enrolled when it's created. Also, regularly deleting VMs creates orphaned device records in Intune until they're [cleaned up](../governance/configure-cleanup-rules).
- Windows Autopilot Self-deploying and pre-provisioning deployment types aren't supported because they require a physical Trusted Platform Module (TPM).
- Out of Box Experience (OOBE) enrollment isn't supported on non-persistent VMs that can only be accessed by using RDP (such as VMs that are hosted on Azure). This restriction means:
- Windows Autopilot and Commercial OOBE aren't supported.

    - Enrollment Status Page isn't supported.

## Configuration

Intune doesn't support any configuration that utilizes a Trusted Platform Module or hardware management, including:

- [BitLocker settings](../device-configuration/overview#endpoint-protection)
- [Device Firmware Configuration Interface settings](../device-configuration/overview#bios-configuration-and-dfci)

## Reporting

Intune automatically detects virtual machines and reports them as "Virtual Machine" in **Devices** &gt; **All devices** &gt; choose a device &gt; **Overview** &gt; **Model** field.

Deallocated virtual machines may contribute to noncompliant device reports because they're unable to [check in with the Intune service](../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

## Retirement

If you only have RDP access, don't use the [Wipe action](../device-management/actions/wipe). The Wipe action deletes the virtual machine's RDP settings and prevents you from ever connecting again.

## Limitations

Intune does not support using a cloned image of a computer that is already enrolled. This includes both physical and virtual devices such as Azure Virtual Desktop (AVD). When device enrollment or identity tokens are replicated between devices, Intune device enrollment or synchronization failures will occur.

- For more information, see [Mobile device enrollment - Windows Client Management](/en-us/windows/client-management/mobile-device-enrollment) and [Certificate authentication device enrollment - Windows Client Management](/en-us/windows/client-management/certificate-authentication-device-enrollment).
- For information on disabling token roaming in AVD, see [Using Azure Virtual Desktop multi-session with Microsoft Intune](azure-virtual-desktop-multi-session#prerequisites).
- For information on troubleshooting issues related to image cloning, see [Error hr 0x8007064c: The machine is already enrolled](/en-us/troubleshoot/mem/intune/troubleshoot-windows-enrollment-errors#error-hr-0x8007064c-the-machine-is-already-enrolled).