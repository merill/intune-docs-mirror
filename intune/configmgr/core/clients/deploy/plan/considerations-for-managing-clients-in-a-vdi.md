---
layout: Conceptual
title: Manage VDI clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/considerations-for-managing-clients-in-a-vdi
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
description: Manage Configuration Manager clients in a virtual desktop infrastructure (VDI).
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 64816b5c-5fa3-8dc2-4d5a-ca2c75a46f4a
document_version_independent_id: 16b9cf72-8c54-6e3c-9988-e4a49450c169
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/considerations-for-managing-clients-in-a-vdi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/considerations-for-managing-clients-in-a-vdi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/considerations-for-managing-clients-in-a-vdi.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: 3335d739-fb99-a71a-c11e-d7c52ea6d07e
---

# Manage VDI clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager supports installing the Configuration Manager client on the following virtual desktop infrastructure (VDI) scenarios:

- **Personal virtual machines**: The virtual machine (VM) maintains user data and settings between sessions.
- **Remote Desktop Services sessions**: Host multiple, concurrent client sessions on a centralized server. Users connect to a session and run applications on that server.
- **Pooled virtual machines/Non-Persistent**: The VM doesn't persist between sessions. When a user closes a session, the virtual environment discards all data and settings. Pooled virtual machines are useful when you can't use Remote Desktop Services. For example, if a required application can't run on the Windows Server that hosts the client sessions.
- **Azure Virtual Desktop**: A desktop and app virtualization service that runs on Microsoft Azure. Starting in version 1906, use Configuration Manager to manage these virtual devices running Windows in Azure.

## Personal VMs

Configuration Manager treats personal VMs the same as a physical computer. You can preinstall the Configuration Manager client on the VM image or after you provision it.

For more information, see [Support for virtualization environments](../../../plan-design/configs/support-for-virtualization-environments).

## Remote Desktop Services

You don't install the Configuration Manager client for individual Remote Desktop sessions. Install it once on the server that hosts Remote Desktop Services. You can use all Configuration Manager client features on the Remote Desktop Services server.

For more information, see [Welcome to Remote Desktop Services](/en-us/windows-server/remote/remote-desktop-services/welcome-to-rds).

## Pooled VMs/Non-Persistent

When you decommission a pooled virtual machine, any changes made by Configuration Manager are lost.

Because the VM might only be operational for a short length of time, some Configuration Manager features may not return relevant data. For example, hardware inventory, software inventory, and software metering. Consider excluding pooled VM from inventory tasks.

## Azure Virtual Desktop

For more information, see [Supported operating systems for clients and devices](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices#azure-virtual-desktop).

## Other considerations

Because virtualization supports running multiple Configuration Manager clients on the same physical computer, many client operations have a built-in randomized delay for scheduled actions. For example, hardware and software inventory, antimalware scans, software installations, and software update scans. This delay helps distribute the CPU processing and data transfer for a server that has multiple VMs that run the Configuration Manager client.

Except for Windows Embedded clients in servicing mode, Configuration Manager clients not in virtualized environments also use this randomized delay. This behavior helps avoid peaks in network bandwidth. It also reduces the CPU processing on site systems, such as the management point and site server. The delay interval varies according to the Configuration Manager capability. For example, see [About client settings - Disable deadline randomization](../about-client-settings#disable-deadline-randomization).

To help with Configuration Manager client performance in virtual environments that support multiple user sessions, it disables user policy by default. Starting in version 1910, you can enable user policy in this scenario. For more information, see [About client settings - Enable user policy for multiple user sessions](../about-client-settings#enable-user-policy-for-multiple-user-sessions).